# Deploy-a-high-availability-web-app-using-CloudFormation

### Project Overview
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


### How to run the supporting material?

You can run the supporting material in two easy steps:
- Ensure that the AWS CLI is configured before running the command below
- Check the region in the create.sh file
- Create the network and server infrastructure
./create.sh myFirstStack final-project.yml server-parameters.json

To make an update
- Change the AMI ID and key-pair name in the servers.yml
- Check the region in the update.sh file
./update.sh myFirstStack final-project.yml server-parameters.json



