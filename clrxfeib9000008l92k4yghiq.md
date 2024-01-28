---
title: "Terraform in details"
datePublished: Sun Jan 28 2024 11:37:04 GMT+0000 (Coordinated Universal Time)
cuid: clrxfeib9000008l92k4yghiq
slug: terraform-in-details
tags: variables-in-terraform

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