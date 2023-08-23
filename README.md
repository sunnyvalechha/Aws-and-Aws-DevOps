# Aws_notes
Aws Step by Step Practicals

* There are four components of IAM
  1. User
  2. Groups
  3. Roles
  4. Policies


• User:- One user is a one physical person.
• Group:- Group our user into groups as Developers, Administrators, Finance, Platfrom Support. We should create a group for every function and put your relevant user into the group as a 
  industry best practises.
• Roles:- Iam Roles is a secure way to interact with any kind of service in Aws, It allows 1 part of Aws to access another part of Aws.
• Policies:- 

# Securing Root Account
• AWS root account is the email address you used to sign up for AWS. The root account has full Adminstrative access to Aws. For this reason, it is important to secure this account.

Security Identity & Compliance > IAM Dashboard > Add MFA for root user > give device name (any) > use google authenticator as device > next > show QR code > put code into both boxes from the mobile device auth tool > add MFA.

![image](https://github.com/sunnyvalechha/Aws_notes/assets/59471885/8f8e6da6-0191-4d7a-8f67-616ffbbe2617)
![image](https://github.com/sunnyvalechha/Aws_notes/assets/59471885/02fa9fa6-e555-4a10-bdad-ce02baae3771)
![image](https://github.com/sunnyvalechha/Aws_notes/assets/59471885/41833d1c-bfbd-47b1-bbe9-ddbb9c14b3a2)

# Method 2 

• In account details > Security Credentials > Add MFA device

![image](https://github.com/sunnyvalechha/Aws_notes/assets/59471885/fa1e440a-a959-4864-b940-377260ac4e44)
![image](https://github.com/sunnyvalechha/Aws_notes/assets/59471885/2e92497d-ead2-4b06-abd1-c7a98add4d03)

# Roles Practical
Create user
Access Type 	- Programmtic Access
Attach Policies - S3 full access
Create user
Save Credentials

Create Instance
Type - aws configure
copy & paste - access key & secret access key 
aws s3 ls 
ls -a 
.aws 
cd .aws
cat credentials (this file should not be here)
rm -rf credentials
aws s3 ls - permissions denied

Go to Roles
Create Role
EC2
Next: permissions
S3 Full Access
create role

Select Instance
Instance Settings - Attach Iam Role
Instance - aws s3 ls (will work now)

# Policies 
* Single policy or multiple Policies can be assigned to the user, group and roles.
* Following Industry's best practises we don't assign policy directly to a user. We will add user into a group and assign policy to the group.
* Policies are like permissions on AWS
* There are three types of IAM policies in AWS

a. Managed Policies - Created & Administered by Aws only, we cannot change managed policies. A single managed policy
	can be attached to multiple users, groups & roles within and accross accounts.
	
b. Customer Managed Policies - We create this policy, Apply to multiple users, groups & roles, In our account only.
	Can maintain upto 5 versions of this policy.

c. Inline Policy - Managed by us but only apply single user, group & role, If we delete user, group or role
	this policy will no longer available.

 Managed Policies:-
 (a. ![image](https://github.com/sunnyvalechha/Aws_notes/assets/59471885/5a760b47-379f-4d37-a3d7-53efbfffca2c)

 Customer Managed:-
 (b. ![image](https://github.com/sunnyvalechha/Aws_notes/assets/59471885/f503500f-3929-4906-922a-54d15d388de9)

Taking example of S3 service 
![image](https://github.com/sunnyvalechha/Aws_notes/assets/59471885/e8d7d530-4bd3-4d6d-a1f6-a236dc6a23f5)

We can add more Permissions


