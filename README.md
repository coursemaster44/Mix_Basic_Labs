
# Lab1

EC2 Lab With Manual Apache
------------------------------

**Step 1.Goto AWS Management Console>AWS Services>Find services>Type EC2>Click on EC2>EC2 Dashboard>Instances>Launch Instances**

**Step 2.Choose AMI(Amazon Machine Image) Amazon linux 2 AMI Free tier eligible,Click to Select**

**Step 3.Choose Instance type**
 - Type t2.micro Free tier 
 - vCPUs-1 
 - Memory-1Gib

Click on Next-Configure Instance details

**Step 4.Configure Instance details**
- Number of Instances- type 1
- Network-Default VPC
- Subnet- No preference
- Auto assign Public IP-Use Subnet setting (Enable)
- IAM Role
- User Data

  Click on Next:Add Storage

**Step 5. Next Add Storage**
- Keep Default Size-8 Gib

  Click Next:Add Tags

**Step 6. ADD Tags**
  Leave as of now
  
  Click on Next:Configure Security Group

**Step 7.Configure Security Group**
 -SSH already there
 -Add Rule for HTTP

Click Review and Launch >Launch

**Step 8. Review**
Select an existing key pair or create a new key pair

- Select create a new pair
- Provide key pair name
- Click on Download key pair 
- Launch instance

**Step 9. Click on the launched Instance and Click on Details to see the Public IP and other details.**

**Step 10. Ec2 dashboard>Instances>Launched Instance>Actions>Connect**

**Step 11. Run the Following Commands**

```sh
$ sudo su
$ yum update -y
$ yum install -y httpd
$ systemctl start httpd.service
$ systemctl enable httpd.service
$ echo "Hello World from $(hostname -f)" > /var/www/html/index.html
$ cd /var/www/html
$ ls -a
$ echo "Hello World from $(hostname -f)" > /var/www/html/index.html
$ ls -a
$ cat index.html
```

**Step 12. Copy the Public IP and paste in the browser to see Apache Web server is Running**

### End Of Lab






# Lab2

Ec2 Lab With User Data Apache
------------------------------

**Step 1. Goto AWS Management Console>AWS Services>Find services>Type EC2>Click on EC2>EC2 Dashboard>Instances>Launch Instances**

**Step 2.Choose AMI(Amazon Machine Image) Amazon linux 2 AMI Free tier eligible,Click to Select**

**Step 3.Choose Instance type**
 - Type t2.micro Free tier 
 - vCPUs-1 
 - Memory-1Gib

Click on Next-Configure Instance details

**Step 4.Configure Instance details**
- Number of Instances- type 1
- Network-Default VPC
- Subnet- No preference
- Auto assign Public IP-Use Subnet setting (Enable)
- IAM Role
- Advance Details>User Data
    - Select As Text

```sh
#!bin/bash
yum update -y
yum install -y httpd
systemctl start httpd.service
systemctl enable httpd.service
echo "Hello World from $(hostname -f)" > /var/www/html/index.html
```

  Click on Next:Add Storage

**Step 5.Next Add Storage**
- Keep Default Size-8 Gib

  Click Next:Add Tags

**Step 6. ADD Tags**
  Leave as of now
  
  Click on Next:Configure Security Group

**Step 7.Configure Security Group**
 -SSH already there
 -Add Rule for HTTP

Click Review and Launch>Launch

**Step 8. Review**
Select an existing key pair or create a new key pair

- Select create a new pair
- Provide key pair name
- Click on Download key pair 
- Launch instance

**Step 9. Click on the launched Instance and Click on Details to see the Public IP and other details.**

**Step 10. Ec2 dashboard>Instances>Launched Instance>Actions>Connect**

**Step 11. Copy the Public IP and paste in the browser to see Apache Web server is Running**

### End Of Lab





# Lab3

### lab3-ElasticBeanStalk
-----------------------------------------------------------------------------------------------------------------------------------------------------------

**Step 1. Goto AWS Management Console>AWS Services>Find services>Type Elastic Beanstalk>Click on Elastic Beanstalk>Elastic Beanstalk>Create Application**


**Step 2. Create a Web App**
   - Application Name-MyfirstEbsapp
		 
		 - Platform 
		    - Platform 
		       - Node.js
			- Platform branch
			   - Node.js 12 running on 64bit Amazon Llinux2
			- Platform version
			   - 5.2.3(Recommended)
			   
	  
   - Application Code
			   - Select Sample application
			 
	
 Click on Create Application.
	


**Step 3. Creating environment started**

Elastic BeanStalk launches an environment named MyfirstEbsapp-env with these AWS resources:

 - S3 Bucket

 - Target Group

 - Security Group for ec2 instance
 
 - Security Group for ALB
 
 - Auto Scaling launch configuration
 
 - Auto Scaling Group
 
 - Auto Scaling Policies
 
 - CloudWatch Alarms
 
 - Load Balancer
 
 - Load balancer listener

 - EC2 instance


**Step 4. Check the environment**

- The environment overview pane shows its URL,current health status, the application version,platform version  

- Click on MyfirstEbsapp>Application versions

- Click on MyfirstEbsapp-env

Click on Go to environment



**Step 5. Goto each component and verify the resources created by Elastic BeanStalk**

``` 
   - S3 Bucket
        -Goto AWS Console>All Services>S3>Buckets
        
   
   - Auto Scaling launch configuration
         - AWS Console>Services>Ec2>Auto Scaling>launch configuration>User Data>View User Data
         
		
   - Auto Scaling Group
         - AWS Console>Services>Ec2>Auto Scaling>Auto Scaling Groups
         
		 
   - EC2 instance
         - AWS Console>All services>EC2 >Instances>    
         
		
   - Target Group
         - Goto AWS Console>All Services>EC2>Load Balancer>Target Group>Targets
		 
   
   - Load Balancer
         - AWS Console>Services>EC2>Load Balancing>Load balancers>awseb-AWSEB-LoadBalancer>Listeners>Edit
         
	
  -  Security Groups
         - Goto AWS Console>All Services>EC2>Security Groups
         
		 
  -  CloudWatch Alarms
         - AWS Console>Services>CloudWatch>Alarms>Alarm	 
		 
```


**Step 6.ElasticBeanStalk>Applications>MyfirstEbsapp>Application versions**

  - Click on Sample Application>nodejs.zip
  
  - Download the nodejs.zip
  
  
  
  # End of Lab
  

lab4#ElasticBeanstalk-2
--------------------------------------------------------------------------------------------------------------------------------------------------

**Step 1. Open node.js in VS studio and do changes for background color**

**Step 2. Save this file as nodejs2.zip**

**Step 3.Elastic BeanStalk>Applications>MyfirstEbsapp>Application versions>upload>Sample application-1>choose file>nodejs(2).zip>upload**

**Step 4.Select Sample application-1>Actions>Deploy>Deploy**

**Step 5.Open VS Studio>index.html>Terminal**

```sh
zip -r dir.zip . -x "_MACOSX"
```

**Step 6.MyfirstEbsapp>Application versions>upload>Sample application-2>choose file>dir.zip>upload**

**Step 7.Select Sample application-2>Actions>Deploy>Deploy**

**Step 8.ElasticBeanStalk>Environments>Myfirstebsapp-env>Events**

**Step 9.ElasticBeanStalk>Environments>Myfirstebsapp-env**

 - Click on Application URL 
 
 **Step 10.Elastic BeanStalk>Applications>MyfirstEbsapp>Actions>Create Environment>Web server environment>select**
 

# End of Lab

# lab5#Git-Installation-lab
----------------------------------------------------------------------------------------------------------------------------------------------
### Run the following commands to install Git.

``` sh
$ git --version
$ brew update && brew upgarde
$ brew install git
$ brew link --force git
$ git --version
```
# End of Lab




# lab6#ALB Lab-1
-----------------------------
**Step 1. Go to AWS Console>All Services>EC2>Load Balancing>Target Groups>Create Target Group**

**Step 2. Specify group details as following**
-   Select Instances in target type  
-   Target group name as MyFirstTargetgroup
-   Protocol-HTTP,Port-80
-    VPC-Default
-    Protocol version
-    Health Checks
	  - Health check protocol- HTTP
	   - Health check path- /
		  
**Now Click on Next**

**Step 3. Register targets**
          
 - Select the available instances
- Ports for the selected instances-80
- Click on "Include as pending below"
		   
**Now Click on Create target group**
		   
**Step 4. "MyFirstTargetgroup" Target Group has been created**

**Step 5. Goto MyFirstTargetgroup>Targets**
              
 - Status is showing "unused"
			  
**Step 6. Go to AWS Console>All Services>EC2>Load Balancing>Load Balancers>Create load balancer**

**Step 7. Click on Create in Application Load Balancer**

**Step 8. Configure Load Balancer as following**
		 
- Basic Configuration
	- Name- MyFirstALB
	- Scheme- internet-facing
	- Ip address type- ipv4
-  Listeners-Protocol-HTTP,Port-80
-  Availability Zones
		      - VPC-Default
			  - Availability Zones-Select all Zones 
-  Configure Security Settings

**Step 9.Configure Security Groups** 
          
-  Create a new security group
	- Type-Custom TCP
    - Protocol-TCP
    - Port Range-80	
    - Source-Custom(0.0.0.0./0)	

Click on Next:Configure Routing

**Step 10.Configure Routing**
          
- Target group- Select Existing target group Name-MyFirstTargetgroup
		  
Click on Register Targets

**Step 11.Click on Next:Review**

**Step 12.Click on Create**
Click on Close

**Step 13.Go to AWS Console>All Services>EC2>Load Balancing>Load Balancers**

**Step 14. Copy the DNS name from Description**

**Step 15. Paste the DNS name in Internet Browser**
           
- Hit refresh 3 times to see the Traffic is going on all the 3 instances

**Step 16.Go to AWS Console>All Services>EC2>Load Balancing>Load Balancers>MyFirstALB>Listeners**

- Select listener and Click on Edit
		   
**Step 17. Go to AWS Console>All Services>EC2>Load Balancing>Load Balancers>Target groups>MyFirstTargetgroup>Targets**	  


Lab7# ASG-Lab
---------------------------------
**Step 1 .Goto AWS Console>EC2 Dashboard>Instances>Lunch Templates>Create launch template**
**Step 2 .In Create Lunch template give as following-**
- Launch template name-MyFirstTemplate

- Amazon Machine image(AMI)-Amazon Linux 2

- Instance type-t2.micro

- key pair-select your key

- Virtual Private Cloud

- Security groups

- Storage

- Advanced details
 - User data
``` sh
#!bin/bash
yum update -y
yum install -y httpd
systemctl start httpd.service
systemctl enable httpd.service
echo "Hello World from $(hostname -f)" > /var/www/html/index.html
```

Click on Create Lunch template>View Launch templates

**Step 3. Select "MyFirstTemplate" Goto Actions>Create Auto Scaling group**

**Step 4.Give name "MyFirstASG" in Auto Scaling group name**
 Click on Next
 
 **Step 5.Network**
 - VPC-default
 - Subnets-Select all the 3 subnets
 
 Click on Next
 
 **Step 5.Load balancing**
 -No Load balancer for as of now
 
 Now Click on Next
 
 **Step 6.Configure group size and scaling policies**
 - Group size
   - Desired capacity-1
   - Minimum capacity-1
   - Maximum capacity-1
   
 - scaling policies-None
 
 Click on Next
 
**Step 7.Add Notifications**
 Click on Next
 
**Step 8.Add Tags**
 Click on Next
 
**Step 9.Review**
 Click on Create Auto Scaling group
 
**Step 10 Select MyFirstASG>Instances>Lifecycle**
- Status-InService
 
**Step 11.Copy the Instance Ip Address and paste in Internet browser**

**Step 12.EC2>Auto Scaling groups>MyFirstASG>Edit**

**Step 13. Change Group size**
- Desired capacity-3
- Minimum capacity-3
- Maximum capacity-3

**Step 14.EC2>Auto Scaling groups>MyFirstASG>Instances>Lifecycle**

**Step 15. Goto EC2 Dashboard>Instances**

Copy the Ip address of all the three Instances and paste it in Internet Browser one by one.
 
 # End of Lab
 
 
 # Lab8-ASG&ALB
-------------------------------------------------------------------
**Step 1. Goto AWS Console>All Services>EC2>Load Balancing>Load Balancers>MyFirstALB>Listeners**

**Step 2. EC2>Auto Scaling groups>MyFirstASG>Edit**
- Go to Load Balancers and select the Application or Network Load Balancer target groups
- Select "MyFirstTargetgroup"
- Health check type
  - Select ELB 
  - Put the value to 120 sec of Health check grace period.

Now Click on Update

**Step 3.EC2>Auto Scaling groups>MyFirstASG>Instance management**
- See all instances are InService

**Step 4.Select 1st Instance>Actions>Security>Change security groups**
- Remove "launch-wizard-1" security group
- Add "port80closed" security group

**Step 5. EC2 Dashboard>Network & Security>Security Groups>port80closed>Inbound rules**

**Step 6. Select 1st Instance>Security>Inbound rules**

**Step 7. EC2 Dashboard>Load Balancing>Target Groups>Targets**
- Wait for Instance to become unhealthy

**Step 8.EC2>Auto Scaling groups>MyFirstASG>Lifecycle**
- See that Instance is Terminating
- Now see new Instance is launching.

**Step 9. Copy the Newly launched Instance's IP address and paste in the internet browser**
- See Hello World message.

# End of Lab


# Lab 9--AWS Account SetUp

**Step 1.Open up your browser and type- setting up your AWS free Tier account**
**Step 2.Click on the first result**
**Step 3.Then Click on Create a Free Account**
**Step 4.Provide the following details-**
- Email address
- Password
- Confirm password
- AWS account name

Click on Continue

**Step 5.Now again give some more details-**
- Account type
- Full name
- Company name
- Phone number
- Country/Region
- Address
- City
- State
- Postal code

Click on Create account and continue

**Step 6.Payment Information details-**
- Credit/Debit card number
- Expiration date
- Cardholder's name
- Billing address

**Step 7.Authenticate Transaction with OTP**

**Step 8.Confirm your identity with following-**
- Text message/Voice call
- Country/Region code
- Cell Phone Number
- Security check

Click on Send SMS

**Step 9.Enter verification code**
Click on Verify Code 

**Step 10. Your identity has been verified successfully**
Click on Continue

**Step 11. Select a Support Plan**
- Select Free

**Step 12.Fill the details before it will ask you to sign in to AWS Console**
- My Role is:Academic/Researcher
- I am interested in:Devops

Click on Submit
See Thank You message.

**Step 13.Click on Sign in to the Console**

**Step 14.Sign in page-**
- Provide Root user email address.

Click on Next

**Step 15.Type the password**
Click on Signin

Our Free Tier AWS Acoount is Ready.


# End of Lab

# Lab10
# IAM-User-setup

**Step 1.Login to AWS Console>Click on Your AWS Account>My Billing Dashboard>Billing preferences**

**Step 2.Under Billing Preferences-**
- Select Receive Free Usage Alerts
- Mention Email address
- Select Receive Billing Alerts

Click on Save preferences.

**Step 3.Goto AWS Console>All Services>CloudWatch>Billing**
- Please Switch Region to # US East(N.Virginia) as CloudWatch displays all billing data
and alarms in # US East(N.Virginia)

**Step 4.Billing>Create Alarm>Conditions**
- Threshold type - Static
- Whenever EstimatedCharges is.. - Greater
- than - 5 USD

Click on Next

**Step 5.Configure actions>Notification**
- Alarm state trigger - In alarm
- Select an SNS topic>Create new topic
    - topic name - Default_CloudWatch_Alarms_Topic
	- Provide Email address to receive the notification.
	Click on Create Topic
	
	Now Click on Next
	
**Step 6.Add name and description**
- Alarm name - MyBillingAlarm
- Description

Click on Next

**Step 7.Preview all the details and Click on Create Alarm**
- Successfully created MyBillingAlarm

**Step 8.Goto your Email inbox and look for the email from AWS**
- Open Email and click on Confirm Subscription
- See the message Subscription confirmed

**Step 9. AWS Console>All services>IAM>IAM Dashboard>Users>Add user**
- Set User details-Provide User name
- Select AWS access type 
  - Access Type
     - Programmatic access
     - AWS Management Console access
	 
 - Console password
  
 Click on Next:Permissions
 
 **Step 10.Click on Attach existing policies directly**
 - Select AdministratorAccess
 
 Click on Next:Tags
 
 **Step 11.Click on Next:Review**
 
 **Step 12.Review your choices and Click on Create user**
 
 **Step 13.Click on Download.csv**

# End of Lab




		   		  



























