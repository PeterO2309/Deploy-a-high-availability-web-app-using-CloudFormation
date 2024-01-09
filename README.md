# Deploy-a-high-availability-web-app-using-CloudFormation

## Project Overview
This project is a simplified Instagram clone (developed using JavaScript, and HTML), deployed to an Apache Web Server running on an EC2 instance.

It comprises of two parts:
- Diagram: a visual aid to understand the CloudFormation script.

<img alt="infrastructural diagram" src="screenshots/INFRASTRUCTURAL DIAGRAM.png">

- Script (Template and Parameters): CloudFormation script that interprets the instructions.


### Dependencies
1. AWS account
You would be required to have an AWS account to build cloud infrastructure.
2. VS code editor
An editor would be helpful to visualize the image as well as code. Download the VS Code editor here.
3. An account on www.lucidchart.com
A free user account on www.lucidchart.com is required to be able to draw the web app architecture diagrams for AWS.


## How to run the supporting material?

You can run the supporting material in two easy steps:
- Ensure that the AWS CLI is configured before running the command below
- Check the region in the create.sh file
- Create the network and server infrastructure.
  
```./create.sh myFirstStack final-project.yml server-parameters.json```

To make an update
- Change the AMI ID and key-pair name in the servers.yml
- Check the region in the update.sh file.
  
```./update.sh myFirstStack final-project.yml server-parameters.json```


## Steps Taken

1.	Created a VPC
•	It will accept the IP Range -also known as the CIDR block- from an input parameter
2.	Created and attached an Internet Gateway to the VPC
3.	Created two public and two private subnets within the VPC with Name Tags to call them “PublicSubnet1”, “PublicSubnet2”, “PrivateSubnet1” and “PrivateSubnet2”.
•	These will also need input parameters for their ranges, just like the VPC.
4.	NAT Gateways are deployed in each public subnet.
•	This will require you to allocate an Elastic IP that you can then use to assign it to the NAT Gateway.
5.	The Public Subnets have the MapPublicIpOnLaunch property set to true. You can use this reference for help.
6.	The Private Subnets have the MapPublicIpOnLaunch property set to false.
7.	All subnets need to be /24 in size.
•	For assistance with IP math, you can use a subnet calculator such as this one.
8.	We created three Routing Tables (one for the public subnet and two for the two private subnets). 
9.	Created a Route in the Public Route Table to send default traffic (0.0.0.0/0) to the Internet Gateway we created. Associated the public subnets to the routing table. 
10.	Create a Route in the Private Route Table to send default traffic ( 0.0.0.0/0) to the NAT Gateway.  Did this for PrivateRouteTable1 and PrivateRouteTable2. NatGateway1 and NatGateway2 were added respectively to the private Route Tables. Likewise, PrivateSubnet1 and PrivateSubnet2 were associated with the RouteTables respectively. 

11.	Since we will be downloading the application archive from an S3 Bucket, we created an IAM Role allowing our instances to use S3 Service. See https://www.radishlogic.com/aws/cloudformation/cloudformation-ec2-with-iam-role-template/ for more details. 
12.	We created two security groups, one for a load balancer in public subnet and another for the web servers in private subnets.
13.	Our application is deployed into private subnets with a Load Balancer in the public subnet. We created a Launch Configuration for our application servers to deploy four servers, two located in each of the private subnets. Requirements: two vCPUs and at least 4GB of RAM. The Operating System to be used is Ubuntu. We have allocated at least 10GB of disk space. 
14.	We created an Auto-Scaling Group which uses the Launch Configuration for scaling up our servers to a minimum of 4 and a maximum of 5. The configuration of the EC2 instance that spins up automatically, if required, as a part of the autoscaling group resides in a launch configuration.
15.	Created a Load Balancer for our application with a listener rule associated with a target group comprising of the public subnets.  Port 80 is used in Security Group#s, health checks and listeners associated with the load balancer. 
16.	Finally, once you execute this CloudFormation script, you should be able to delete it and create it again, over and over in a predictable and repeatable manner, this is the true verification of working Infrastructure-as-Code

