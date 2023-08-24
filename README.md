# Aws_notes | Aws Step by Step Theory and Practicals

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

$ To create a user > IAM Dashboard > Users > Create user > provide username > 'Provide user access to Aws management console' > 'I want to create an IAM user' > 'Untick for create new password at every sign In' > add user to group > if group not exist, create group > It will show as mentioned in snap 5 > checkout other details under "security credentials" like MFA, 'Access Keys', 'Code commit' >  We need to add user into the group created manually > To add permissions > go to permissions under user > add permissions > attach policy > provide admin access > 

![image](https://github.com/sunnyvalechha/Aws_notes/assets/59471885/f838c49f-6ffb-4445-b5c4-33b1236c7230)
![image](https://github.com/sunnyvalechha/Aws_notes/assets/59471885/4efb629a-b27f-4858-ad35-32d532dcd2cc)
![image](https://github.com/sunnyvalechha/Aws_notes/assets/59471885/ba3f19fe-7d28-40a8-a145-90d20431fac8)
![image](https://github.com/sunnyvalechha/Aws_notes/assets/59471885/47604c1f-5256-4f42-a76f-2ddac4abda36)

![image](https://github.com/sunnyvalechha/Aws_notes/assets/59471885/a7d4c5e8-8729-46ce-827c-0f9722bd033c)
![image](https://github.com/sunnyvalechha/Aws_notes/assets/59471885/53529776-fc58-4b52-a82f-67ea50ac3556)
![image](https://github.com/sunnyvalechha/Aws_notes/assets/59471885/3ece9667-32c8-434e-b5b7-1fede003f9d9)
![image](https://github.com/sunnyvalechha/Aws_notes/assets/59471885/0733cf74-527a-4e06-a1df-2a2f8f0e2487)
![image](https://github.com/sunnyvalechha/Aws_notes/assets/59471885/baa347a0-4c1d-4293-bed2-a7f1132a127e)
![image](https://github.com/sunnyvalechha/Aws_notes/assets/59471885/ae046366-c65e-4b81-b389-8df63def3e08)
![image](https://github.com/sunnyvalechha/Aws_notes/assets/59471885/5361a8f6-9ce3-43a2-a0a1-7743e2cbfdc0)









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


