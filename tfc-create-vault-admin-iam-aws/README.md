
# Creating a Vault Admin IAM User in AWS Master Account

In this blog, we will walk through the steps to create a Vault Admin IAM User in the AWS Master Account using Terraform. This user will have permissions necessary to manage IAM users and their policies, specifically for Vault.

## Prerequisites

- AWS CLI configured with appropriate permissions.
- Terraform installed and configured.

## Instructions

### Step 1: Define IAM User Resource

1. Create an IAM user named `vault_admin`.
2. Set the user's path to `/`.
3. Add a tag with the user's name.

### Step 2: Create IAM Access Key for the User

1. Generate an access key for the `vault_admin` user.
2. Configure the lifecycle to ignore changes to the `user` attribute.

### Step 3: Define Inline Policy Document

1. Create an inline policy document.
2. Allow the following IAM actions:
    - AttachUserPolicy
    - CreateUser
    - CreateAccessKey
    - DeleteUser
    - DeleteAccessKey
    - DeleteUserPolicy
    - DetachUserPolicy
    - GetUser
    - ListAccessKeys
    - ListAttachedUserPolicies
    - ListGroupsForUser
    - ListUserPolicies
    - PutUserPolicy
    - AddUserToGroup
    - RemoveUserFromGroup
3. Restrict the policy to resources matching the pattern `arn:aws:iam::YOUR_AWS_ACCOUNT_ID:user/vault-*`.

### Step 4: Attach Inline Policy to User

1. Attach the inline policy to the `vault_admin` user.
2. Use the name `vault-admin-policy` for the policy.

### Step 5: Define Outputs

1. Output the following information:
    - Vault Admin IAM User ID
    - Vault Admin IAM User ARN
    - Vault Admin IAM User Name
    - Vault Admin IAM User Access Key ID
    - Vault Admin IAM User Secret Access Key (mark as sensitive)
    - Vault Admin IAM User Encrypted Secret Access Key

### Step 6: Define Variables

1. Define a variable for the IAM user name with the default value `vault-admin`.
2. Define a variable for the inline policy name with the default value `vault-admin-policy`.

## Applying the Configuration

1. **Initialize Terraform**: 
   ```bash
   terraform init
   ```

2. **Validate the Configuration**: 
   ```bash
   terraform validate
   ```

3. **Terraform Plan**
```
terraform paln
```


4.  **Apply the Configuration**: 
   ```bash
   terraform apply
   ```

After running these commands, the Vault Admin IAM User will be created with the necessary permissions and access keys.



