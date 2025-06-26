# Deployed a Website to AWS EC2 Using GitHub Actions and Nginx

This project demonstrates how to automate the deployment of a website to an 
AWS EC2 instance using GitHub Actions and Nginx.


It showcases a practical CI/CD pipeline where code is pushed to the 
GitHub repository is automatically deployed to a configured EC2 server via SSH.


## Tech Stack

- AWS EC2 (Ubuntu Server)
- GitHub Actions (CI/CD)
- Nginx (Web Server)
- SSH Key for Authenticating into EC2

## Deployment Architecture



## 🚀 Features

- Push to GitHub → Auto deployment to EC2
- Nginx reverse proxy configuration
- GitHub Actions workflow file for seamless CI/CD
- Basic setup for security and permissions

## 📝 Medium Article

Read the full step-by-step tutorial here:  
👉 [Deployed a Website to AWS EC2 Using GitHub Actions and Nginx](https://medium.com/@josephinennamani/deployed-a-website-to-aws-ec2-using-github-actions-and-nginx-9be95a0e2d38)

## 📂 File Structure




 
An Elastic IP address was attached to the EC2 instance to enable a static IP address.
Since no domain is purchased for our web application
The setup ensures a seamless and repeatable deployment process, 
eliminating the need for manually editing the code and deploying to the server. 
Nginx is used as a web server to host the website, ensuring the efficient delivery of content to end-users.

Kindly refer to the PNG file in the file directory to see the full architectural design
Thank
