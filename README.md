# Deploy-a-high-availability-web-app-using-CloudFormation

### Project Overview
This project is a simplified Instagram clone (developed using JavaScript, and HTML), deployed to an Apache Web Server running on an EC2 instance.

It comprises of two parts:
- Diagram: a visual aid to understand the CloudFormation script.

<img alt="infrastructural diagram" src="screenshots/INFRASTRUCTURAL DIAGRAM.png">

- Script (Template and Parameters): CloudFormation script that interprets the instructions.


### Prerequisites:
- AWS Account
- Student-ready starter code - Download and unzip this file via https://drive.google.com/file/d/15vQ7-utH7wBJzdAX3eDmO9ls35J5_sEQ/view.

### Topics Covered:
- S3 bucket creation


###Dependencies
1. AWS account
You would be required to have an AWS account to build cloud infrastructure.

2. VS code editor
An editor would be helpful to visualize the image as well as code. Download the VS Code editor here.

3. An account on www.lucidchart.com
A free user account on www.lucidchart.com is required to be able to draw the web app architecture diagrams for AWS.


###How to run the supporting material?
You can run the supporting material in two easy steps:
# Ensure that the AWS CLI is configured before running the command below
# Create the network infrastructure
# Check the region in the create.sh file
./create.sh myFirstStack network.yml network-parameters.json
# Create servers
# Change the AMI ID and key-pair name in the servers.yml
# Check the region in the update.sh file
./update.sh mySecStack servers.yml server-parameters.json

## Table of Contents

- [Create S3 Bucket](#create-s3-bucket) 
- [Upload files to S3 Bucket](#upload-files-to-s3-bucket)
- [Secure Bucket via IAM](#secure-bucket-via-iam)
- [Configure S3 Bucket](#configure-s3-bucket)
- [Distribute Website via CloudFront](#distribute-website-via-cloudfront)
- [Access Website in Web Browser](#access-website-in-web-browser)


## Create S3 Bucket

1. Navigate 
