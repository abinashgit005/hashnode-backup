---
title: "Ansible"
datePublished: Tue Jan 16 2024 19:08:12 GMT+0000 (Coordinated Universal Time)
cuid: clrgq8g2r000a08jvei6o8zuq
slug: ansible
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1705515480133/cfc7fd1c-86ac-40d1-842a-fb943d579c4d.jpeg
tags: ansible, ansible-playbook, ansible-module, ansible-conditionals

---

Here is a basic understanding of ansible configuration file, playbooks, modules, Handlers, Roles, Collections, and jinja2 Templates.

### Ansible Configuration File

when you install, it creates a default configuration at the location :- **/etc/ansible/ansible.cfg**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1705429294058/82110c31-3220-443d-96bf-070e6c329ae8.png align="center")

but what if you want your custom config file outside of your playbook file ?  
you can place your config file outside of your playbook file and specify the location of this configuration file through an environmental variable before running the ansible playbook.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1705429617741/51d5dcf3-3f59-4b6e-987b-ff6af18eb1fb.png align="center")

```yaml
ANSIBLE_CONFIG=/opt/ansibleweb.cfg ansible-playbook playbook.yaml
```

this time when a playbook runs, this time it will pick the custom config file.

and suppose you have configured all these files with different values for different different parameters, then which files will have what priority ?

the first priority will be for the configuration file you are specifying through environment variables

followed by the **ansible.cfg** in the current directory, where the ansible playbooks are running and then followed by the **.ansible.cfg** file in user home directory  
and last the **default configuration** file.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1705431421248/20b1e65c-95ea-4fce-9e9c-30692f366928.png align="center")

Also if you want to change a single parameter for your playbook you can over-write the single parameter value by an environment variable.  
you can set it up just right before executing the ansible playbook.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1705431948551/22a6c774-696a-4e46-bea8-6bc9a54d5e86.png align="center")

```yaml
ansible-config list # to list all config files
ansible-config view # shows the current config file
ansible-config dump # shows the current settings
```

### Ansible Inventory

Ansible needs to establish connection with the servers to work with them. There is no need of any agent to be installed in the target servers , That's why ansible is agentless. for Linux servers ansible use SSH based connectivity whereas for windows servers ansible use PowerShell remoting.

The Information about the target machines are being stored in an Inventory File. Ansible has it's default Inventory file located at /etc/ansible/hosts and if you don't create any new inventory file, ansible use it's default inventory file. we can specify our target machines in the inventory file

```yaml
[common]
database_server1.learning.com
Loggingserver2.learning.com
webserver3.learning.com

[database]
database_server1.learning.com
database_server2.learning.com
database_server3.learning.com

[messaging]
messaging_server1.learning.com
messaging_server1.learning.com
messaging_server1.learning.com
```

we can add alias name for the servers by using **ansible\_host** parameter.

```yaml
database ansible_host=database_server1.learning.com
```

**ansible\_host** is ana inventory parameter used to specify the FQDN or IP address of a server

#### Inventory parameters

there are multiple ansible inventory parameters are available.

ansible\_connection-ssh/localhost/winrm  
ansible\_port-22  
ansible\_usr-root-admin  
ansible\_ssh\_pass-mypassword

#### Inventory formats

1. INI
    
2. yaml
    

yaml format : Its more structured.

```yaml
all:
   childeren:
       database:
             hosts:
                  database_server1.learning.com
                  database_server2.learning.com
                  database_server3.learning.com
        messaging:
              hosts:
                  messaging_server1.learning.com
                  messaging_server1.learning.com
                  messaging_server1.learning.com
```

### Verifying playbooks

we can use check mode and diff mode to verify our ansible playbooks.  
**check:**  
Using this mode you can do the DRY RUN of your playbook and no actual modification happens here.

```yaml
ansible-playbook install-nginx.yml --check
```

<mark>Note: all ansible modules does not support check mode. If a task uses a module that does not support check mode then task will be skipped when you run the playbook in check mode.</mark>

\*\*diff:  
\*\*Using diff mode you can check the difference in playbook before and after changing

```yaml
ansible-playbook install-nginx.yml --diff
ansible-playbook install-nginx.yml --check --diff # check and diff option both
```

**Syntax check:**  
This helps us to ensure our playbook syntax is error free.

```yaml
ansible-playbook install-nginx.yml --syntax-check
```

ansible-lint:  
It checks our code for potential issues, bugs and stylistic errors etc.

```yaml
ansible-lint install-nginx.yml
```

## Conditions:

we can use conditional statements like when to execute a particular task if the condition satisfies.

```yaml
---
- name: install-nginx
  hosts: all
  tasks:
    - name: install nginx on debian
      apt:
        name: nginx
        state: present
      when: ansible_os_family == 'Debian' and
            ansible_distribution_version == "16.04"
    - name: install nginx on Redhat
      apt:
        name: nginx
        state: present
      when: ansible_os_family == 'Redhat' or 
            ansible_os_family == 'SUSE'
```

we can use variables as well.

```yaml
---
- name: install-multiple-packages.yml
  hosts: all
  vars:
    packages:
      - name: nginx
        required: True
      - name: mysql
        required: True
      - name: apache
        required: False
   tasks:
     - name: install "{{item.name}}" on Debian
       apt:
         name: "{{item.name}}"
         state: present
       when: item.required == True
       loop: "{{ packages }}"
```

**register:**

to record a output of one task we can use register directive. and we can use this for next task as required.

```yaml
---
- name: send a email if service is down
  hosts: all
  tasks:
    - name: check service status
      command: service httpd status
      register: result 
    - name: send an email
        to: abinashmishra@005gmail.com
        subject: service alerts
        body: http is down
      when: result.stdout.find('down') != -1
```

### ansible facts

Variables related to remote systems are called facts in ansible. ansible facts are system defined variables that can be used in the playbooks. To see all available facts, add this task to a play:

```yaml
- name: Print all available facts
  ansible.builtin.debug:
    var: ansible_facts
```

ansible facts collects information about the server during the execution of the playbook.

```yaml
- name: install nginx
    apt:
       name: nginx=1.18.0
       state: present
    when: ansible_facts{os_family} == 'Debian' and ansible_facts{distribution_major_version} == '18'
```

another example:

```yaml
- name: start service 
   service: 
       name: abiapp
       state: started
   when: environment == 'production'
```

### loops:

loop is a looping directive that executes same task multiple number of times. Each time it runs, It store value of each item in the loop in a variable named item. and then you can simply replace the user name as variable like this '{{ item }}' general way:

```yaml
- name: create users
   hosts: localhost
   tasks:
       user: name=abi             state: present
       user: name=krishna      state: present
       user: name=john           state: present
```

**using loops:**

```yaml
- name: create users
  hosts: localhost
  tasks:
   - user: name='{{ item.name }}' state: present UID: '{{ item.UID }}'
     loop:
       - name: abi
          UID: 1234
       - name: krishna
          UID: 0001
       - name: john
          UID: 4567
```

**with\_\***

```yaml
- name: create users 
  hosts: localhost
  tasks:
   - user: name='{{ item.name }}' state: present UID: '{{ item.UID }}' 
     with_item:
        - name: abi
           UID: 0002
        - name: krishna 
           UID: 0001
        - name: john 
           UID: 4567
```

many other options:

```yaml
with_file
with_url
with_mangodb
with_env
with_filetree
```

\## Modules  
**Idempotency:**  
An action which, when performed multiple times, has no further effect on its subject after the first time it is performed.

command:  
executes a command on a remote node.

```yaml
- name: add dns entry to resolve.conf
  host: localhost
  tasks:
   - name: execute a command
     command: date
   - name: display a file content
     command: cat abc.txt
```

script:

service:

lineinfile:  
This module search for a line in a file and replace it or add if doesn't exist.

```yaml
- name: add dns entry to resolve.conf
  host: localhost
  tasks:
   - linefile:
       path: /etc/resolve.conf
       line: nameserver 10.250.0.1
```