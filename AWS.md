## AWS Organizations

- Create and manage multiple AWS accounts
  - Log in via "Switch Role"
  - OrganizationAccountAccessRole - default

- IAM Identity Center
  - fka "AWS SSO"
  - Free Service
  - Enable > Create User > Sign on using [access portal](https://d-9067efe4f4.awsapps.com/start/#/)
  - Create Permission Sets > Predefined permission set > AdministratorAccess / PowerUserAccess / ReadOnlyAccess / ViewOnlyAccess / etc.
  - Groups connect permission sets with users
    - Create Group > AWS Accounts > Assign users and groups
  - Make the access portal url nicer:
    - IAM Identity Center > Setting > Identity Source > Actions > Customize AWS access portal URL



## AWS CLI

See [AWS CLI](Environment%20and%20Terminal.md#AWS-CLI)

### Logging on with SSO

- Directly via access portal UI: Access portal > Access Keys > Copy/Paste
- CLI First: `aws configure sso --profile personal`
  - SSO session name (Recommended): personal
  - SSO start URL [None]: https://rhett.awsapps.com/start/
  - SSO region [None]: us-east-1 
    - Should be wherever IAM Identity Center is enabled
  - Validate using `aws sts get-caller-identity -- personal`
- Name profiles the same thing across team
- Login: `aws sso login --profile personal`
- Switch roles: `aws configure sso --profile personal`

## Misc
- Can use ["Multi-Account Containers" via Firefox](https://www.youtube.com/watch?v=mgoVhOW3Qfc) to sign into multiple accounts at the same time.