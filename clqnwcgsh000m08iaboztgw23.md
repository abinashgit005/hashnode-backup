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
    
2. It records all the resources we have provisioned with terraform in a JSON format with in the terraform.tfstate file as a representation of the real world(here it means the the resources we craeted in the cloud provider).
    

Caution

Never delete or manipulate the terraform.tfstae file by yourself.

## terraform commands

### terraform init

### terraform plan

### terraform apply

### terraform destory

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

provisioners are used to run some command in local / remote machines as a part og resource creation or deletion,

#### Usefulness :

bootstrap a resource  
configuration mgmt.  
Cleanup before delete etc...