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

## File Structure
The structure of your basic website can look like this
```
my-website/
│
├── index.html
├── styles.css
└── .github/
 └── workflows/
 └── deploy.yml
```
However, mine looks like what you have below because I needed something beautiful that I could tweak for myself. :)
![](/screenshots/File%20tree.png)

## Configure your GitHub Secrets
From your GitHub, go to Secrets and Variables, under actions, add the following secrets. 
EC2_HOSTyour EC2 public IP address, EC2_USER: usually ubuntu, then your EC2_SSH_KEY: copy the entire content of your
.pem, which is your keypair from your EC2 instance, for authenticating via SSH.
![](/screenshots/Secret%20Variables.png)

## The GitHub Actions Workflow
In .github/workflows/deploy.yml here is where the magic happens, which is the deployment. Study the code below

[View Workflow File](.github/workflows/deploy.yml)

----------------------------------------

![](/screenshots/Success.png)

## Final Output
And this is what our final website template looks like. I will just go ahead to modify this website for myself. 
You can go further with the project by adding SSL for HTTPS.
![](/screenshots/website%20deplpyed.png)

## 📝 Medium Article

You can also read the full step-by-step tutorial here:  
👉 [Deployed a Website to AWS EC2 Using GitHub Actions and Nginx](https://medium.com/@josephinennamani/deployed-a-website-to-aws-ec2-using-github-actions-and-nginx-9be95a0e2d38)






 
NB: An Elastic IP address was attached to the EC2 instance to enable a static IP address.
Since no domain is purchased for my web application, and I wanted a stable IP address, 
I can simply memorize. It also ensures a seamless and repeatable deployment process, 
eliminating the need for manually editing the code and deploying to the server. 
Nginx is used as a web server to host the website, ensuring the efficient delivery of content to end-users.


# Thank You
