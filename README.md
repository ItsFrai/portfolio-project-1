# Portfolio Project 1 — Automated Cloud Deployment

## What This Project Does
A fully automated web application deployment on AWS using Infrastructure as Code and containerization. Running one command provisions a cloud server, installs Docker, and deploys a containerized web application — no manual configuration required.

## Technologies Used
- **AWS EC2** — Cloud compute instance
- **Terraform** — Infrastructure as Code to provision AWS resources automatically
- **Docker** — Containerized web application
- **Docker Hub** — Public image registry to store and distribute the Docker image
- **Nginx** — Web server running inside the container

## Architecture
1. Terraform provisions an EC2 instance and security group on AWS
2. A startup script (user_data) runs on first boot and installs Docker
3. Docker pulls the custom image from Docker Hub
4. Nginx serves the web application inside the container
5. The application is accessible publicly via the instance IP on port 80

## How To Deploy
1. Clone this repository
2. Configure AWS credentials on your machine
3. Navigate to the terraform folder
4. Run `terraform init`
5. Run `terraform apply`
6. Visit the IP address shown in the output

## What I Learned
- Writing Terraform configurations to automate AWS infrastructure
- Building and pushing custom Docker images to Docker Hub
- Bootstrapping EC2 instances automatically using user_data scripts
- Configuring AWS security groups for network access control
- Combining Infrastructure as Code with containerization in a real deployment
