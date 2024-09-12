---
title: "Terraform in details"
datePublished: Sun Jan 28 2024 11:37:04 GMT+0000 (Coordinated Universal Time)
cuid: clrxfeib9000008l92k4yghiq
slug: terraform-in-details
tags: variables-in-terraform, lifecycle-rule-in-terraform, terraform-validation

---

Here we can go through terraform features and other aspects of terraform

## Terraform variables validation

we have applied the validation parameter for the resource group name, if the given name won't meet the desired conditions it will through error.

```yaml
variable "rg_name" {
    type = string
    default = "rg-13"

    validation {
      condition = length(var.rg_name) > 3 && substr(var.rg_name, 0, 3) == "rg-"
      error_message = "resource group must start with \"rg-\" "
    }
}
```

when you try to run terraform plan

```yaml
terraform plan -out tfplan -var rg_name="tfrg"
```

Error:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1706441319120/dde5088a-674e-42e4-b886-cbfae9f2d1f0.png align="center")

### Lifecycle rules:

###   
create\_before\_destroy:

Using lifecycle rules in terraform you can control how terraform create and destroy resources.  
suppose you changes vm image which eventually delete the old resource and create a new one. by using lifecycle rules you can define how to control this

```yaml
resource "azurerm_resource_group" "example" {
  # ...

  lifecycle {
    create_before_destroy = true
  }
}
```

Now when you run terraform apply command, the new resource will be created first and then the old resource will be deleted.

### Prevent destroy:

If you don’t want to destroy the resource you can specify as below:

```yaml
resource "azurerm_resource_group" "example" {
  # ...

  lifecycle {
    prevent_destroy = true
  }
}
```

here terraform avoid to delete the resource and this can help you when someone accidentally delete any resource especially databases.  
  
***<mark>This property doesn’t make resources immune to the terraform destroy command. It will only prevent resource deletion from changes made to the configuration file and subsequent terraform apply.</mark>***

Ignore Changes:

This rule will prevent a resource from being updated based on a list of attributes we defined inside the life cycle block

suppose a tag got changes by someone but this change has no much impact on the resource so this change can be ignored.  
also you can use ignore\_changes = all if you don’t want the resource to be modified for any changes.

```yaml
resource "aws_instance" "example" {
  # ...

  lifecycle {
    ignore_changes = [
      # Ignore changes to tags, e.g. because a management agent
      # updates these based on some ruleset managed elsewhere.
      tags,
    ]
  }
}
```