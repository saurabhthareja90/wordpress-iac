# wordpress-iac
Installs and deploys WordPress into Dev and Prod environments on to Amazon EC2 instances in an Auto Scaling group with a multi-AZ Amazon RDS database instance for storage in Prod environment and single AZ RDS database instance for dev environment.

<h1><b>Prerequisite</b></h1> -

1. AWS Account - please follow the steps mentioned in - https://docs.aws.amazon.com/polly/latest/dg/setting-up.html to create an AWS account and an IAM user if not already created.
Note: Download the CSV file generated for the IAM user as contains the Secret Access Key and Credential required to configure AWS in Step 3.

2. Install awscli - install awscli on local machine by following instructions provided on - https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-install.html

3. Configure awscli - configure awscli on local machine by following instructions provided on - https://docs.aws.amazon.com/cli/latest/reference/configure/

commands used - aws configure

4. Latest version of Ansible is installed by following instructions provided on - https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html

5. Create an ssh keypair in AWS account under EC2 -> Network & Security -> Key Pairs which will be required to connect to EC2 instances later. Name the key - amazon-servers, download.



* [Create cloudformation stack](https://console.aws.amazon.com/cloudformation/home?region=ap-southeast-2#/stacks/new?stackName=wordpress-app&templateURL=https://s3-ap-southeast-2.amazonaws.com/saurabh-public-artifacts/wordpress-app.template) 
