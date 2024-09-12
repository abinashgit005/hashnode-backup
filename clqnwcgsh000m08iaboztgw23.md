---
title: "Terraform"
seoTitle: "terraform"
seoDescription: "terraform"
datePublished: Wed Dec 27 2023 14:53:58 GMT+0000 (Coordinated Universal Time)
cuid: clqnwcgsh000m08iaboztgw23
slug: terraform
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1703688661906/c1e8c124-2d9a-4a71-afe1-7761f8f7815c.jpeg
tags: terraform

---

### create a terraform block to create a git repo.

```yaml
provider "github" {
    token = "ghp_Ne9Xu2Tpzic7txSxxxxxxxxxxxxxxxxxxxYYYYYYYYYla"
}

resource "github_repository" "terraform_repo" {
  name        = "terraform_repository"
  description = "My awesome terraform repo"
  visibility = "public"
  auto_init = true
}
```

### variables file

To set a lots of variable, we need a variable definations file. Terraform loads automatically the variable defination file if the file name ends with ".tfvars" and ".tfvars.json" also if the file name ends with ".auto.tfvars" and ".auto.tfvars.json"

### .tfstate file

1. when we create a configuration file to privision our infrastructure, terrafom automatically create a terraform.tfstate file in the local workspace to manage the record. It also determine which part already has been created and which part terraform should create.
    
2. It records all the resources we have provisioned with terraform in a JSON format with in the terraform.tfstate file as a representation of the real world(here it means the the resources we created in the cloud provider).
    

Caution

Never delete or manipulate the terraform.tfstae file by yourself.

## terraform commands

### terraform init:

Terraform init command will check the configuration file and initialise the working directory that contains .tf file

It understands the types of provider we have declared in the resource type and then downloads the plugin to work on the resources declared in the .tf file.

### terraform plan:

This command allow us to review all the actions will be done to create the declared resources, but it does not create the resource.

### terraform apply:

when we run terraform apply command it actually creates the resources .  
Before that it's again allow us to review and asking for confirmation as yes/no ?  
we can bypass it by using --auto-approve

### terraform destroy

### terraform validate

to validate the code.

### terraform refresh

terraform refresh checks if any deviation in the state file with the real infrastructure and updates in the state file. It does not modify the real infrastructure by any means.

Important

Suppose you have 2 resources and want to destroy one resource, then you can use terraform target "resource\_type"."resource name"

### terraform console

This can be used for debugging purpose. If you want to print any variable to check the value in the current directory, you can use terraform console and exit command to exit from the console.

### terraform fmt

terraform fmt command is used to rewrite Terraform configuration files to a canonical format and style.

### terraform taint

terraform taint command marks a resource as tainted. It doesn't make changes in the real infrastructure but in the .tfstate file it marks the resource as tainted so that when you hit terraform plan/apply command next time it will destroy and recreate the resource.

### Provisioner

provisioners are used to run some command in local / remote machines as a part of resource creation or deletion,

#### Usefulness :

bootstrap a resource  
configuration mgmt.  
Cleanup before delete etc...

## Terraform Module

By using terraform module we can reuse the ready made infrastructure code. we can create our own custom modules or we can use modules from terraform registry itself.

[Azure Modules](https://registry.terraform.io/namespaces/Azure)

we have lots of modules in terraform registry such as azure vnet module, azure compute module, azure naming module etc...

### Terraform Import

suppose you have created any resource manually via GUI or command line. Now you want to manage those resources with terraform. This scenario can be done by the help of Terraform import.

**Example:**  
you have created a storage account manualy and want to manage with terraform.  
first create storage account configuration file in your main.tf file and then try the terraform import command

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1706367238306/8b8ecd08-5a27-434b-9ce4-7c4d6664a3b0.png align="center")

terraform import command output:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1706367473848/cc33b797-78cf-40e8-b464-38d0bc6ad1cd.png align="center")

If you wont add your storage account configuration file you will get error like below:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1706367561848/e8cdff73-26f4-4c17-9e32-24eeabde9c84.png align="center")