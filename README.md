# wordpress-iac
Installs and deploys WordPress into Dev and Prod environments on to Amazon EC2 instances in an Auto Scaling group with a multi-AZ Amazon RDS database instance for storage in Prod environment and single AZ RDS database instance in dev environment.

<h1><b>Prerequisites</b></h1>

1. AWS Account - please follow the steps mentioned in - https://docs.aws.amazon.com/polly/latest/dg/setting-up.html to create an AWS account and an IAM user if not already created.
Note: Download the CSV file generated for the IAM user as contains the Secret Access Key and Credential required to configure AWS in Step 3.

2. Install awscli - install awscli on local machine by following instructions provided on - https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-install.html

3. Configure awscli - configure awscli on local machine by following instructions provided on - https://docs.aws.amazon.com/cli/latest/reference/configure/

commands used - aws configure

4. Latest version of Ansible is installed by following instructions provided on - https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html

5. Create an ssh keypair in AWS account under EC2 -> Network & Security -> Key Pairs which will be required to connect to EC2 instances later. Name the key - amazon-servers, download.

<h1><b>Architecture Diagram</b></h1>

![alt text](https://raw.githubusercontent.com/saurabhthareja90/wordpress-iac/master/Wordpress-app-blueprint.png)

<h1><b>Templates </b></h1> -

Install application from console using the templates - 

1. [Create resources stack](https://console.aws.amazon.com/cloudformation/home?region=ap-southeast-2#/stacks/new?stackName=resources-stack&templateURL=https://s3-ap-southeast-2.amazonaws.com/saurabh-public-artifacts/resources-stack.template)
    Click on the the link above to install prerequisite resources in AWS account. Clicking on the link above will take you through to cloudformation console, follow the steps in console and create stack. Resources stack creates underlying networking resources e.g. - VPC, Subnets, RouteTables, InternetGateway, NAT Gateway etc. 

2. [Create app stack](https://console.aws.amazon.com/cloudformation/home?region=ap-southeast-2#/stacks/new?stackName=app-stack&templateURL=https://s3-ap-southeast-2.amazonaws.com/saurabh-public-artifacts/app-stack.template) 
    Once resources-stack is finished creating, click on the link above to create app stack. App stack creates application resources e.g. - EC2 instances, Launch Configurations, ASG, SecurityGroups, ALB, TargetGroup, RDS etc.

    Application stack CloudFormation template lets you select certain application parameters as shown below - 

    ![alt text](https://raw.githubusercontent.com/saurabhthareja90/wordpress-iac/master/parameters.png)



3. Once app stack creation is finished, go to output section of app-stack and go to WebsiteURL mentioned, it should load the        highly scalable, highly available wordpress website.
