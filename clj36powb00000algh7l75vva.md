---
title: "Azure AD intro with Terraform examples"
seoTitle: "Azure AD intro with Terraform"
datePublished: Mon Jun 19 2023 18:23:05 GMT+0000 (Coordinated Universal Time)
cuid: clj36powb00000algh7l75vva
slug: azure-ad-intro-with-terraform-examples
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1687198428340/3f987f73-ae3b-46d8-b55e-02eeb917eda8.png
tags: cloud, azure, cloud-computing, devops, terraform

---

## **Introduction**

Azure Active Directory (Azure AD) offers organizations a comprehensive cloud-based solution for efficient directory and identity management. With its array of features, including username and password management, role and permissions control, multi-factor authentication, and application monitoring, Azure AD is an indispensable tool for businesses of all sizes. This article explores the key aspects of Azure AD, starting with user management, followed by administrative units, and concluding with group management.

## Terraform setup for Azure AD

First, we need to specify the providers that we are going to use so that Terraform knows which providers it needs to download.

```json
terraform {
    required_providers {
        azuread = {
            source  = "hashicorp/azuread"
            version = "~> 2.15.0"
        }
    }
}

provider "azuread" {
    tenant_id = "<your_azure_account_tenant_id>"
}
```

If we run `terraform init` command after adding the above code to any of the files ( `providers.tf` is a preferred name ) in the terraform directory, it downloads the required providers.

For whatever code we use in this article to work, we need to authenticate to our Azure account so that the changes we create in code will actually happen. The easiest and recommended way to authenticate for Terraform is through service principal and client secret.

To create one service principal, we need to have a Contributor role for Azure AD. If we have that, we can create a service principal using the command `az ad sp create-for-rbac --role="Contributor" --scopes="/subscriptions/<your-subscription-number>"` in Azure CLI which can be downloaded from [https://learn.microsoft.com/en-us/cli/azure/install-azure-cli](https://learn.microsoft.com/en-us/cli/azure/install-azure-cli) here if you haven't already. This will return a response containing 4 important fields which we want. They are id ( subscription\_id ), tenant\_id, client\_id, and client\_secret. It is better to create a bash file which contains the following contents.

```bash
export ARM_CLIENT_ID="<client_id>"
export ARM_CLIENT_SECRET="<client_secret>"
export ARM_TENANT_ID="<tenant_id>"
export ARM_SUBSCRIPTION_ID="subscription_id"
```

Run this script before running any plan. Now, we have the setup ready and we can move on. If you get any error during the creation of the service principal, check your permissions and if your permissions are fine, it might have created the principal but still threw the error as happened in my case.

## **Managing Users in Azure AD**

Azure AD provides robust user management capabilities that enable organizations to efficiently create and oversee user identities in the cloud. Here are some essential aspects of managing users in Azure AD:

### **User Properties**

1. **User Profile**: Each user has a profile that contains basic information such as their name, email address, and contact details.
    
2. **Assigned Roles**: Users can be assigned specific roles within the organization, granting them access to various resources and services based on their responsibilities.
    
3. **Administrative Units**: Azure AD allows for the grouping of users based on geographical or organizational units, facilitating streamlined user management. Administrative Units (AUs) enable organizations to assign specific administrators to oversee users from particular regions or units.
    
4. **Group Membership**: Users can be part of different groups within Azure AD, allowing for efficient management of permissions and access rights.
    
5. **Applications**: Azure AD enables the assignment of applications to users, granting them access to specific software and services.
    
6. **Licenses**: Users can be assigned licenses that provide access to specific features or services within Azure AD.
    
7. **Devices**: Azure AD associates devices with user accounts, providing information about the devices and their join type, such as Azure AD join or hybrid Azure AD join.
    
8. **Role Assignments**: User roles define the resources to which a user has access, specifying their permissions and privileges.
    
9. **Authentication Methods**: Azure AD supports various authentication methods, allowing users to choose the method that best suits their needs.
    

## Creating a user with Terraform

```json
resource "random_password" "test" {
    length           = 16
    special          = true
    override_special = "!#$%^&*[]{}()"
}

resource "azuread_user" "test" {
    user_principal_name   = "<email-format-with-domain-specific-to-your-azure-account>"
    display_name          = "test"
    password              = random_password.test.result
    force_password_change = true
    given_name            = "article"
    surname               = "terraform"
}
```

Terraform forces us to provide a password for every user. So, I am using this random password generator first, getting a random password from it [https://registry.terraform.io/providers/hashicorp/random/3.0.0/docs/resources/password](https://registry.terraform.io/providers/hashicorp/random/3.0.0/docs/resources/password) and passing it to the user. I am also forcing the user to change the password when they first try to log in so that no one can see the password from the terraform state. Only the first 3 fields in the above "azuread\_user" block are necessary and others are optional. I added "given\_name" and "surname" blocks to help in the group creation which is coming next.

You can check more options that can be provided while creating the user here [https://registry.terraform.io/providers/hashicorp/azuread/latest/docs/resources/user](https://registry.terraform.io/providers/hashicorp/azuread/latest/docs/resources/user) .

## **Streamlining User Management with Administrative Units**

Azure AD introduces the concept of Administrative Units (AUs) to simplify user management and enable efficient delegation of administrative responsibilities. AUs are particularly useful for grouping users based on specific regions or organizational units. Here's what you need to know about Azure Administrative Units:

1. **Efficient User Grouping**: AUs help organize users based on geographical or organizational criteria, allowing administrators to manage users from specific regions or units more effectively.
    
2. **Assigning Administrators**: Within each Administrative Unit, administrators can be assigned specific roles to perform tasks relevant to their areas of responsibility. These roles include Authentication admin, Groups admin, Help desk admin, License admin, Password admin, and User admin.
    

By utilizing Azure Administrative Units, organizations can streamline user management, delegate administrative responsibilities, and ensure efficient control over user access and permissions based on specific regions or organizational units.

AUs require a premium tier account and I don't have one. So I m not able to show you a tested terraform example here.

## **Simplifying User Collaboration with Azure AD Groups**

Azure AD groups provide a convenient way to manage and organize users within an organization, promoting collaboration and resource sharing. There are two primary types of groups in Azure AD:

1. **Security Groups**: Security groups are used to grant permissions to a set of users for specific cloud resources. They streamline access control and simplify user management by providing a collective set of permissions to a group of users.
    
2. **Microsoft 365 Groups**: Microsoft 365 groups facilitate collaboration by providing access to shared resources such as calendars, mailboxes, and more. They enable users to work together seamlessly on projects and initiatives.
    

Azure AD allows for different methods of grouping users into security groups:

1. **Assigned Grouping**: Users can be manually assigned to a group, providing direct control over group membership.
    
2. **Dynamic User Grouping**: Grouping users dynamically involves setting parameters based on user properties, and automatically adding or removing users from the group based on predefined criteria.
    
3. **Dynamic Device Grouping**: Similar to dynamic user grouping, dynamic device grouping involves setting parameters based on device properties, and automatically grouping devices based on predefined criteria.
    

Azure AD group properties and functionalities include:

* **Overview**: Basic information about the group, including membership type and unique identifier.
    
* **Properties**: Group details such as name, type, description, and other relevant attributes.
    
* **Members**: Users who are part of the group.
    
* **Owners**: Administrators with control over the group and its settings.
    
* **Administrative Units**: Association of groups with specific AUs for streamlined management.
    
* **Group Memberships**: Hierarchical grouping of groups within other security groups.
    
* **Applications**: Assignment of applications to groups for collective access to services.
    
* **Licenses**: Group-level assignment of licenses for consistent access to licensed features.
    
* **Role Assignments**: Resources accessible to group members, defining permissions and privileges.
    
* **Dynamic Membership Rules**: Configuration rules for automatic group membership updates based on criteria and properties.
    

## Creating groups with Terraform

```json
resource "azuread_group" "test" {
    display_name     = "test"
    security_enabled = true
    dynamic_membership {
        enabled = true
        rule    = "user.surname -eq \"terraform\""
    }
}
```

The "display\_name" and either "security\_enabled" or "mail\_enabled" being true are required and all others are optional. To add users to a group depending on a condition, we use "dynamic\_membership" which takes a rule according to which it groups users. Here, I am grouping users whose "surname" is equal to "terraform" and hence it adds only the user which we created before to this group.

This also requires a premium plan to work. We can manually add users to a group in the basic tier.

```json
data "azuread_client_config" "current" {}

resource "azuread_group" "test" {
    display_name     = "test"
    security_enabled = true
    members = [
        azuread_user.test.object_id,
        data.azuread_client_config.object_id
    ]
}
```

This way, we can add users manually to a group by specifying their "object\_id" in the members list. The way we fetch already existing data from the cloud to the terraform just to use some details on our current is through a "data" block like how we did in the first line above. In the above code, I am getting the current user who is applying the Terraform plan which is the user associated with the service principal that we created earlier to use with Terraform. And then, I added the object\_id of it in the members list. So, this time, the group contains two users. One is the Terraform user, and the other is the user we created above with Terraform code.

## **Conclusion**

Azure Active Directory (Azure AD) provides a robust and comprehensive solution for directory and identity management in the cloud. By effectively managing users, leveraging Administrative Units, and harnessing the power of Azure AD groups, organizations can streamline user management, delegate administrative responsibilities, and enhance collaboration among users. Azure AD offers a seamless and secure identity management solution that empowers businesses to embrace the cloud and unlock their full potential.

If you find this article helpful and informative, please don't forget to like and share it. Also, follow @[Chiranjeevi Tirunagari](@VChiranjeeviAK) for more such articles. Consider connecting with me on socials at [https://www.linkedin.com/in/vchiranjeeviak/](https://www.linkedin.com/in/vchiranjeeviak/) and [https://twitter.com/vchiranjeeviak](https://twitter.com/vchiranjeeviak) . Thank you.