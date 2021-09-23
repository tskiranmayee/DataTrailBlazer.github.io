---
layout: post
title: Chapter 5 - Securing Your AWS Resources
---
***

## AWS IAM (Identity and Access Management)

***
* Management dashboard (https://console.aws.amazon.com/iam)
* It connects an account to all the administration tools for managing the account security.
* Protect the root user by locking it down( the e-mail id and password to cerate an AWS account for the first time)
* For daya to day administrative work and effective functionality of root user create USERS and GROUPS.

##### Protecting the Root User
* Root user has all the permissions for the AWS resources and authorizing the expenses.
* Active usage of root user is a significant security risk, if compromised in attacks, data will be stolen and the resources will be used my others generating huge bills.
* Protect root  user by 1) Strong Password 2) Multifactor authentication (MFA) 3) use IAM user instead of root user.

##### Authentication
* 3 Ways - 1) management Console 2) Programatic Access 3) Command-line Interface(CLI)
* "who you claim to be"
* management Console -- Provide User ID and passowrd.
* Programatic or CLI Access -- set the access keys.

##### Passwords
* Complex password -- Uppsercase, Lowercase,Numbers, Symbols.
* Use random generated strings
* Never reuse the passwords across multiple accounts.
* Efficient way -- Use a password manager like LastPass, Dashlane, or KeePass2. 
* Create a Password Policy from root user to all the accounts.
* MFA adds second laye of security.
* MFA works with associated physical device - Universal 2nd Factor(U2F) , r MFA-compliant device like YubiKey,  smartphone with the Authenticator app
* Enter with Step 1: Password -> Step 2:Short-lived 6 digit number sent to your MFA device.

##### Access Keys 
*  Programmatic and Command-line access to many AWS resources is authenticated by access keys (without the option of MFA).
*  New set of keys generated AWS Management Console -> Security Credentials page -> Create New Access Key Button->Download the new pair.
*  Security Credentials page - lists all the keys and allows - deactivate, activate or delete existing keys.
*  The root user take the time to delete all keys associated with the root account.

##### Secure Shell Key Pairs
* Encrypting remote login sessions is the Secure Shell (SSH) protocol
* When that “network” is the internet safety of your data is less.

##### Users, Groups, and Roles
* "Principle of Least Privilege" -> assign only priveleges need by users and only if required.

##### IAM User
* Primary Admin (User) to replace root access -> AdministratorAccess policy

##### IAM Groups
* Using groups to administrate the permissions associated with multiple users in batches can get all that done much more efficiently.
* New Employee -> Create New User -> attach to an Appropriate Group -> Automatic inheritance of Policies

##### IAM Roles
* Important for Application Services not Users
* "Trusted Entity"
* Entity -> AWS resources (like EC2) -> 3rd party federated identify provider(like Google)
* 

***
## Providing Federated Access
***
* Security Assertion Markup Language 2.0 (SAML) or Microsoft’s Active Directory into your infrastructure.
* SSO (Single Sign-on)
* AWS Directory Service for Microsoft Active Directory(AWS Microsoft AD)

***
## Credential Report
***
* Download Report button ->CSV -> IAM User, MFA enabled, last logged in, active access keys
* Monitor accoutns for security holes.

***
## Encryption
***
* Encryption Keys -> AWS Key Management System (AWS KMS)
* KMS will apply encryption using a customer master key (CMK)
* Encrypt any data managed by an AWS service, including RDS, DynamoDB, EBS volumes attached to EC2 instances
* S3 encryption -> during or after bucket creation.
* Two ways 1) S3-managed server-side encryption keys (SSE-S3) or 2) KMS-managed keys (SSE-KMS)
* S3 buckets -> server-side encryption
* Data at transit from your local infrastrucutre ->client-side encryption
* Before uploading to S3 -> KMS-managed customer master key or a clientside master key.


***
## Regulatory Compliance (AWS Artifact)
***
* Artifacts -  the service home page is a set of links to documents describing various regulatory standards and how
AWS meets them. Each of those documents is referred to by Amazon as an **Artifact**.
*  U.S. government’s Federal Risk and Authorization Management Program (FedRAMP), the Government of Canada
(GC) Partner Package, and the Australian Prudential Regulation Authority (APRA) “Management of Security Risk in Information and Information Technology”
*  PCI DSS Attestation of Compliance (AOC) and Responsibility Summary for handling credit card transaction data.
*  Service Organization Controls (SOC) 1, 2, and 3 audits of AWS infrastructure.
