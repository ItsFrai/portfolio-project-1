# Portfolio Project 1 — Automated Cloud Deployment Pipeline

## What This Project Does
A fully automated cloud deployment pipeline that eliminates manual server 
configuration. A single command provisions cloud infrastructure, and every 
code change automatically builds, packages, and deploys the application 
without any manual intervention.

## Technologies Used
- **AWS EC2** — Cloud compute instance
- **Terraform** — Infrastructure as Code to provision AWS resources automatically
- **Docker** — Containerized web application for consistent deployments
- **Docker Hub** — Public image registry to store and distribute Docker images
- **GitHub Actions** — CI/CD pipeline that automates build and deployment
- **Nginx** — Web server running inside the container

## Architecture
```
Code Change → GitHub → GitHub Actions → Docker Build → Docker Hub → EC2 Deploy
```
1. Developer pushes code to GitHub
2. GitHub Actions triggers automatically
3. New Docker image is built and pushed to Docker Hub
4. Pipeline SSHs into EC2 and pulls the new image
5. Old container is stopped and removed
6. New container is started with the updated image
7. Website is live with the latest changes

## How To Deploy
1. Create an AWS account and configure credentials with `aws configure`
2. Clone this repository: `git clone https://github.com/ItsFrai/portfolio-project-1.git`
3. Navigate to terraform folder: `cd portfolio-project-1/terraform`
4. Run `terraform init`
5. Run `terraform apply`
6. Visit the IP address shown in the output

## Disaster Recovery
If the server is lost, full recovery takes under 2 minutes:
- Clone the repo
- Run `terraform apply`
- Terraform rebuilds identical infrastructure automatically
- User data script installs Docker and pulls the latest image from Docker Hub

## What I Learned
- Writing Terraform configurations to automate AWS infrastructure provisioning
- Building and pushing custom Docker images to Docker Hub
- Bootstrapping EC2 instances automatically using user_data scripts
- Configuring AWS security groups for network access control
- Building a complete CI/CD pipeline with GitHub Actions
- Combining Infrastructure as Code with containerization for automated deployments
