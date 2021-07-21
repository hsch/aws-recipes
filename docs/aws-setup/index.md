# AWS

For every project, create a new account [in your organisation](https://console.aws.amazon.com/organizations/v2/home).

This separates all projects nicely and also allows for easy clean up at the end of a project or experiment:
Instead of identifying all individual resources that you don't longer need,
just delete the whole account.

Billing is centrally handled through the organisation's root account.
No need to maintain several billing details.

For every new account, do a few things:

- Set the password. I think you need to use the "Forgot Password" link to set the
root account password for the new account.

- Activate 2FA.

- Create an access key. Ideally, you should create a new user with limited permissions,
but updating these permissions or policies every time you try something new can be a burden.
Make a trade-off between security and convenence. 😬

- Create or update `~/.aws/credentials` with the access key:
  ```
  [example]
  region = us-central-1
  aws_access_key_id = ...
  aws_secret_access_key = ...
  ```
  You can switch the AWS CLI and other tools to this profile by calling `export AWS_PROFILE=example`.
  Give it a try by querying the access key:
  ```
  aws iam list-access-keys
  ```
  
- Create an S3 bucket to the Terraform state and other operational objects.
