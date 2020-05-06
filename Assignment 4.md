**Day 4**

Direct communication cannot be established between two services like Ec-2 and S3.
It can be done in two ways:
1. Inside AWS 
2. Outside AWS

## Inside AWS
* IAM(Identity and Access Management) is a web service that helps to securely control access to AWS resources.
* IAM roles are used to provide permissions to access the services.
* Multiple IAM roles cannot be attached to a single instance, but a single IAM role can be attached to multiple instances.

**Steps to create IAM roles** :-
1. Open AWS console and select *Services*.
2. From Services select *IAM*.
3. Select *Roles* and then *Create roles*.
4. Choose use case as *EC2* and click on *Next:Permissions*.
5. Select the policy name *AmazonS3FullAccess* and click on *Next:Tags*.
6. Enter the *Key* and *Value* and click on *Next:Review*.
7. Enter the *Role name* and if required the role description. Click on *Create role*.
8. Role is created.

**Steps to attach IAM role to EC2** :-
1. From Services select *EC2*.
2. Select the instance and click on *Actions*.
3. Go to *Instance settings* and select *Attach/Rename IAM role*.
4. From the dropdown select the IAM role created and click on *Apply*.
5. Role is attached to the instance.

**Commands to run on MobaXterm** :-
aws s3 ls *(bucket name)*
