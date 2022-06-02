## Enterprise-Scale Prerequisites

Enterprise-Scale can bootstrap an entire Azure tenant without any infrastructure dependencies, and the user must first have Owner permission on the tenant *root* before deploying.

*Note: Once you have completed the deployment, you can remove the Owner permission from the tenant root, as it will no longer be needed for any subsequent operations.*

This requires the following:

- A user that is Global Admin in the Azure Active Directory

- Elevation of privileges of this user which grants him/her the “User Access Administrator” permission at the tenant root scope

- An explicit roleAssignment (RBAC) made at the tenant root scope via CLI or PowerShell (Note: There’s no portal UX to make this roleAssignment)

### [](https://github.com/Azure/Enterprise-Scale/wiki/Deploying-Enterprise-Scale-Pre-requisites#elevate-access-to-manage-azure-resources-in-the-directory)Elevate Access to manage Azure resources in the directory

1.1 Sign into the Azure portal as a user being Global Administrator

1.2 Open Azure Active Directory

1.3 Under *Manage*, select *Properties

1.4 Under *Access management for Azure resources,* set the toggle to *Yes

### Grant Access to the User at *tenant root scope “/”* to deploy Enterprise-Scale

You can use either Bash (CLI) or PowerShell to create the roleAssignment for the current user – or a dedicated user – that will do the deployment.

Bash:

```shell
#sign  into AZ CLI, this will redirect you to a web browser for authentication, if required
az login

#assign Owner role to Tenant root scope  ("/") as a Owner (gets object Id of the current user (az login))
az role assignment create --scope '/'  --role 'Owner' --assignee-object-id $(az ad signed-in-user show --query "objectId" --output tsv)
```

Powershell:

```powershell
#sign in to Azure  from Powershell, this will redirect you to a web browser for authentication, if required
Connect-AzAccount

#get object Id of  the current user (that is used above)
$user = Get-AzADUser -UserPrincipalName (Get-AzContext).Account

#assign Owner  role to Tenant root scope ("/") as a User Access Administrator
New-AzRoleAssignment -Scope '/' -RoleDefinitionName 'Owner' -ObjectId $user.Id
```

> Please note: sometimes it can take up to 15 minutes for permission to propagate at tenant root scope. It is highly recommended that you log out and log back in to refresh the token before you proceed with the deployment.*

---

#### Revoke Access to the User at *tenant root scope “/”* to deploy Enterprise-Scale

You can use either Bash (CLI) or PowerShell to remove the roleAssignment for the current user – or a dedicated user – that had deployed ESLZ.

Bash:

```shell
az role assignment delete --assignee username@example.com --role "User Access Administrator" --scope "/"
```

PowerShell:

```powershell
Remove-AzRoleAssignment -SignInName <username@example.com> `
  -RoleDefinitionName "User Access Administrator" -Scope "/"
```
---
**Alternative BASH commands**
## bash
## AZ Role Assignment
az role assignment create  --scope '/' --role 'Owner' --assignee-object-id $(az ad user show -o tsv --query objectId --id '<replace-me>@<my-aad-domain.com>')

## AZ Role Assignment list
az role role assignment list --role "User Access Administrator" --scope "/"

## AZ Role Assignment Delete
az role assignment delete --assignee username@example.com --role "User Access Administrator" --scope "/"

---
