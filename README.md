Step 1 — Clear the current content

In the editor, press:

Ctrl + A

Then Delete.

Step 2 — Paste this README
# AWS CI/CD Pipeline – Automated Web Application Deployment

## Project Overview

This project demonstrates an end-to-end CI/CD pipeline for automatically building and deploying a web application using AWS DevOps services.

Whenever code is pushed to the GitHub `main` branch, AWS CodePipeline automatically triggers the CI/CD workflow:

**GitHub → AWS CodePipeline → AWS CodeBuild → AWS CodeDeploy → Amazon EC2 → Nginx**

The application is deployed to an Ubuntu EC2 instance and served using Nginx.

---

## Architecture

```text
Developer
    |
    | git push
    v
 GitHub
    |
    v
AWS CodePipeline
    |
    v
AWS CodeBuild
    |
    | BuildArtifact
    v
AWS CodeDeploy
    |
    v
Amazon EC2
(Ubuntu + Nginx)
    |
    v
Web Application
Technologies Used
Technology	Purpose
GitHub	Source code repository
AWS CodePipeline	CI/CD orchestration
AWS CodeBuild	Build and validation
AWS CodeDeploy	Application deployment
Amazon EC2	Application server
Nginx	Web server
AWS IAM	Access control
Linux / Ubuntu	Server operating system
Git	Version control
Amazon CloudWatch	Monitoring and logging
Project Structure
aws-cicd-project/
│
├── index.html
├── buildspec.yml
├── appspec.yml
│
└── scripts/
    └── restart_nginx.sh
CI/CD Workflow
1. Developer pushes code
git add .
git commit -m "Update application"
git push origin main
2. GitHub

The source code is stored in GitHub on the main branch.

3. AWS CodePipeline

CodePipeline detects the GitHub change and starts a new pipeline execution.

4. AWS CodeBuild

CodeBuild reads buildspec.yml, validates the application and creates the build artifact.

5. AWS CodeDeploy

CodeDeploy receives the build artifact and uses appspec.yml to deploy the application to EC2.

6. Amazon EC2

The application is deployed to:

/var/www/html

Nginx serves the application on HTTP port 80.

Configuration Files
buildspec.yml

Defines the CodeBuild phases and build commands.

appspec.yml

Defines the CodeDeploy deployment configuration, destination directory and deployment hooks.

restart_nginx.sh

Restarts Nginx after deployment.

#!/bin/bash

systemctl restart nginx

echo "Nginx restarted successfully"
CI/CD Validation

The pipeline was tested using a real application update.

Version 1
DevOps Practice Project
Version 2
DevOps Practice Project - Version 2

The change was committed and pushed to GitHub:

git add index.html
git commit -m "Update application to Version 2"
git push origin main

The GitHub push automatically triggered:

GitHub
   ↓
CodePipeline
   ↓
CodeBuild
   ↓
CodeDeploy
   ↓
EC2
   ↓
Nginx

All pipeline stages completed successfully and Version 2 was displayed by the deployed application.

IAM Configuration

The project uses IAM roles for AWS service access.

EC2 / CodeDeploy Role
CodeDeployEC2Role
CodeDeploy Service Role
CodeDeployServiceRole

IAM permissions allow the AWS services to perform their required CI/CD operations.

CodeDeploy Agent

The CodeDeploy Agent is installed on the EC2 instance.

Check its status:

sudo systemctl status codedeploy-agent

Expected status:

Active: active (running)
Nginx

Check Nginx:

sudo systemctl status nginx

Test the application locally:

curl http://localhost

Restart Nginx:

sudo systemctl restart nginx
Monitoring

Amazon CloudWatch can be used to monitor:

EC2 metrics
CPU utilization
Application logs
CodeBuild logs
CodeDeploy logs
Deployment activity
Troubleshooting
Check Nginx
sudo systemctl status nginx
Check CodeDeploy Agent
sudo systemctl status codedeploy-agent
Test the application
curl http://localhost
Check listening ports
sudo ss -tulpn
Check Git status
git status
Future Improvements

For a production environment, this project can be extended with:

Application Load Balancer
Auto Scaling Group
Multiple Availability Zones
HTTPS using AWS Certificate Manager
Route 53
CloudWatch alarms
IAM least-privilege policies
Terraform infrastructure as code
Docker
Amazon EKS
Trivy security scanning
Prometheus and Grafana
Key Learnings
Git and GitHub
AWS CodePipeline
AWS CodeBuild
AWS CodeDeploy
Amazon EC2
IAM
Linux / Ubuntu
Nginx
CI/CD automation
Deployment troubleshooting
AWS service integration
Author

Sasikumar Venkatesan

DevOps / Cloud Engineering Practice Project

Technologies: AWS | DevOps | CI/CD | Git | GitHub | Linux | Nginx


### Step 3 — Commit it

After pasting, click **Preview** briefly to make sure the Markdown looks formatted.

Then click:

**Commit changes...**

Use:

```text
Commit message:
Add project documentation
