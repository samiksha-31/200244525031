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
**1. Open AWS console and from Services select *IAM*.**

![Step2](https://user-images.githubusercontent.com/63635471/81144274-5528f980-8f91-11ea-8d6f-9c26acc38bd8.png)

**2. Select *Roles* and then *Create role*.**

![Step3](https://user-images.githubusercontent.com/63635471/81144275-565a2680-8f91-11ea-8b62-49db1747c249.png)

**3. Choose use case as *EC2* and click on *Next:Permissions*.**

![Step4](https://user-images.githubusercontent.com/63635471/81144283-58bc8080-8f91-11ea-9518-fec67f24ed81.PNG)

**4. Select the policy name *AmazonS3FullAccess* and click on *Next:Tags*.**

![Step5](https://user-images.githubusercontent.com/63635471/81144302-6114bb80-8f91-11ea-9794-9ebc00aa3655.PNG)

**5. Enter the *Key* and *Value* and click on *Next:Review*.**

![Step6](https://user-images.githubusercontent.com/63635471/81144311-63771580-8f91-11ea-8e65-fed325600f77.PNG)

**6. Enter the *Role name* and if required the role description. Click on *Create role*.**

![Step7](https://user-images.githubusercontent.com/63635471/81144318-670a9c80-8f91-11ea-9f32-c044b218c928.PNG)

**7. Role is created.**

![Step8](https://user-images.githubusercontent.com/63635471/81144326-696cf680-8f91-11ea-923f-4e699c2ee896.PNG)


**Steps to attach IAM role to EC2** :-
**1. From Services select *EC2*.**

**2. Select the instance and click on *Actions*.**

![Step 2 2](https://user-images.githubusercontent.com/63635471/81144251-4c382800-8f91-11ea-91fc-77cb8015a532.PNG)

**3. Go to *Instance settings* and select *Attach/Replace IAM role*.**

![Step 2 3](https://user-images.githubusercontent.com/63635471/81144263-50644580-8f91-11ea-9863-4ab42cd9d45e.png)

**4. From the dropdown select the IAM role created and click on *Apply*.**

![Step 2 4](https://user-images.githubusercontent.com/63635471/81144268-52c69f80-8f91-11ea-9968-38c075caf1b3.PNG)

**5. Role is attached to the instance.**

![Step 2 5](https://user-images.githubusercontent.com/63635471/81144273-53f7cc80-8f91-11ea-9e54-f419b3f0d863.PNG)

**Commands to run on MobaXterm** :-
aws s3 ls *(bucket name)*
