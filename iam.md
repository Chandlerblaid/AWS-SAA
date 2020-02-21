# Identity Access Management (IAM)

## What is IAM?
- Essentially, IAM allows you to manage users and their level of access to the AWS console.
- IAMs are universal; does not apply to regions at this time
## What does IAM give you?
- Centralized control of your AWS account
- Shared Access to your AWS account
- Granular Permissions
- Identity Federation (including Active Directory, FB, LinkedIN, etc.)
- Multifactor Authentication
- Provide tmp access for users/devices and services where necessary
- Alows you to setup your own password rotation services
- Supports PCI DSS compliance
- Integrates w/ many AWS services
## Critical Terms:
- Users
	○ End Users (people)
	○ New Users have no permissions when first created
- Groups
	○ A collection of users under one set of permissions
	○ A way to group users and apply policies to them collectively
- Roles
	○ You create roles and can then assign them to AWS resources
	○ Ex: Ec2 w/ role to write to an s3
- Policies
	○ A document that defines one or more permissions
## Lab:
- Root Account:
	○ Email address you used to sign up w/ AWS
	○ When you login with this you have Root-level access
		□ Unlimited access
	○ Don't want everyone to have this power
	○ Recommended to only log into Root once or twice when necessary, then create users and give them permissions and group them
	○ Use Google authenticator for mfa (multi-factor authentication)
		□ Always set this up for root
- Access Key ID & Secret Access key
	○ Given when you create a new user and issue their permissions/add them to a group
	○ The key necessary to access this account programatically
	○ Just use your username and password when logging into the console
	○ This information is never accessible again after creating the user
		□ Must download/save it
		□ Can regenerate by making the og ones inactive at user -->  security credentials and creating new keys
- Create a Billing Alert
	○ Can have AWS send you an email when your charges exceeds a certain number
	○ More Info
## Quiz:
- Powerusers have access to all services except managing users and groups in IAM
