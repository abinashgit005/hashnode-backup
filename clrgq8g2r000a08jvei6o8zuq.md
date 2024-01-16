---
title: "Ansible"
datePublished: Tue Jan 16 2024 19:08:12 GMT+0000 (Coordinated Universal Time)
cuid: clrgq8g2r000a08jvei6o8zuq
slug: ansible
tags: ansible, ansible-playbook

---

Here is a basic understanding of ansible configuration file, playbooks, modules and ...

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