# Three-Tier Web Application Deployment on AWS using Terraform

![Three-Tier Banner](assets/Three-Tier.gif)

### This architecture are popular pattern and can provide
1. scalability
2. availability
3. security

This design is focusing on seperate an application into three layers, with specific function and independent from other also spreading the application across multiple availability zones and seperate into three layers If any of availability zone is gones down, the application can automatically scale resources to another availibility zone with affecting the rest of the application

Each tier has its own security group (only allows just "necessary" in and out bound to perform specfic tasks).

Front end - Presentation (React.js)
Back end - Business Logic (ExpressJS)
Database - Storage (MongoDB)

# Jenkins Single Node Setup
1. Create Jenkins server on AWS Console 
`Ubuntu 22.04`, Create Security Group: `8080`, `9090`, Storage: `30GB`, Create IAM Instance Profile: `EC2 Access`
User data: `Use file jenkins_user_data_script.sh`
2. Navitage to jenkins dashboard and then install few plugins `AWS Credentials`, `Pipeline: AWS Steps`, `Pipeline: Stage View`, `Terraform`
3. Create Jenkins Global Credentials Kind: `AWS Credentials`, Name: `aws-creds`, Access Key ID & Secret Access Key: `FROM_YOUR_IAM_USER`
4. Navitage to Tools > Terraform installations > Add Terraform > Name: `terrfaorm`, Install dicrectory: `/usr/bin/terraform` (from `whereis terraform` command)
5. Navitage to Dashboard > New Item > Create `Infra-job` Type `Pipeline` > Pipeline script: `Use file jenkins_init_terraform`

# CI/CD using Jenkins and Argo CD

# Monitoring Setup