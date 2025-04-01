# Three-Tier Web Application Deployment on AWS using Terraform

### This architecture is are popular pattern and can provide
1. scalability
2. availability
3. security

This design focuses on separating an application into three layers, with specific functions and independent of each other, spreading the application across multiple availability zones and separating into three layers. If any of the availability zones goes down, the application can automatically scale resources to another availability zone without affecting the rest of the application

Each tier has its security group (only allows "necessary" in and outbound to perform specific tasks).

Front end - Presentation (React.js)
Back end - Business Logic (ExpressJS)
Database - Storage (MongoDB)

# Jenkins Single Node Setup
1. Create a Jenkins server on the AWS Console 
`Ubuntu 22.04`, Create Security Group: `8080`, `9090`, Storage: `30GB`, Create IAM Instance Profile: `EC2 Access`
User data: `Use file jenkins_user_data_script.sh`
2. Navigate to the Jenkins dashboard and then install a few plugins: `AWS Credentials`, `Pipeline: AWS Steps`, `Pipeline: Stage View`, `Terraform`
3. Create Jenkins Global Credentials Kind: `AWS Credentials`, Name: `aws-creds`, Access Key ID & Secret Access Key: `FROM_YOUR_IAM_USER`
4. Navitage to Tools > Terraform installations > Add Terraform > Name: `terrfaorm`, Install dicrectory: `/usr/bin/terraform` (from `whereis terraform` command)
5. Navigate to Dashboard > New Item > Create `Infra-job` Type `Pipeline` > Pipeline SCM: `Jenkins/infra-pipeline/Jenkinsfile`

# Provisioning EKS (2 Worker Node, 1 Jump Server) using Terraform
1. Create an S3 Bucket and, DynamoDB on the AWS Console
2. Run Infra-job Plan, Apply

# CI/CD using Jenkins and Argo CD

# Monitoring Setup
