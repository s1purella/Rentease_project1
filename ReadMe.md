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

![GitHub Actions](screenshots/website%20to%20AWS%20EC2%20using%20Github%20Actions.drawio%20%281%29.png)

##  Set Up Your AWS EC2 Instance
- Launch an Ubuntu EC2 instance.
- Allow inbound HTTP (port 80) and SSH (port 22) in your security group.
- Generate or download your .pem key securely.

## Prepare Your Website Repo
The structure of your basic website can look like this
my-website/
│
├── index.html
├── styles.css
└── .github/
 └── workflows/
 └── deploy.yml
However, mine looks like what you have below because I needed something beautiful that I could tweak for myself. :)
![](/screenshots/File%20tree.png)




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
