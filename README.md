# Cloud Front 

* Cloud Front is a Fast Content Delivery network (CDN).
* A CDN is a system of distributed servers (network) that deliver webpages and other web content like data, videos, applications to a user, based on the geographical locations of the user, the origin of the webpage, and a content delivery server with low latency and high speed.

Latency is the amount of delay (or time) it takes to send information from one point to the next.
* High Latency is Bad 
* Low Latency is Good 


Edge Location – This is the location where content will be cached. This is separate from an Aws Region / AZ. 
Edge Locations are not just read only, we can also write to them with the help of transfer acceleration.
Objects are cached for the life of the Time To Live (TTL)
You can clear cached object, but you will be charged for that. 

Origin – This is the origin of all the files that CDN will distribute. This can be an S3 bucket, an Ec2 instance, an Elastic load balancer or Route 53.

Distributions – This is the name given the CDN which consists of a collection of Edge locations. 

Web Distribution – Typically used for Websites.

RTMP – Used for Media Streaming.
Real Time Messaging Protocol supports streaming of media files using adobe media server, End users view media files using the media player that is provided by cloud front not the locally installed on the device.

**Practicals**

1. Go to S3 - Create a bucket - Put some images in it 
2. Go to CloudFront - It is a Global Service
3. Create Distribution - Web Distribution
	Origin Domain Name - s3 bucket name
	Origin Path -  particular directory in the origin,  beginning with a forward slash (/). 
	Do not add a slash (/) at the end of the path.
	Origin Id - description of the origin
	S3 bucket access - Yes use OAI (bucket can restrict access to only CloudFront)
	Create New Oai - Demo-identity
	Bucket policy - yes, update
	Viewer protocol policy - HTTP and HTTPS
	Settings - Price class - Use all edge locations (best performance)
 
	WAF - Web application firewall is a layer 7 firewall 
	Leave everything as default & create distribution 
	
4. If distribution is deployed 
5. Copy the domain name put name in brower's url /imagename

s3 - Permissions - Bucket policy - Created automatically that CloudFront Origin Access Identity E3QPH46J3EWB79" this entity update bucket content on cloud front 



==============================================================
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


