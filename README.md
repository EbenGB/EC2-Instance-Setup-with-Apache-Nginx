# EC2 Apache/Nginx Setup on AWS

## Description
This project demonstrates how to launch an EC2 instance and configure a basic Apache or Nginx web server to serve a static HTML page.

## AWS Services Used
- Amazon EC2
- Security Groups
- IAM Roles

## Instructions

### 1. Launch an EC2 Instance
- Choose **Amazon Linux 2** as the AMI.
- Use a **t2.micro** instance type (free tier eligible).
- Create or select an existing **key pair** for SSH access.

### 2. Configure Security Group
- Add an **inbound rule** to allow HTTP (port 80) from anywhere.
- Add an inbound rule for **SSH (port 22)** from your IP.

### 3. Use User Data to Install Apache (or Nginx)
Paste the following in the **user-data** section when launching the instance:

#### Apache Example:
```bash
#!/bin/bash
sudo yum update -y
sudo yum install -y httpd
sudo systemctl start httpd
sudo systemctl enable httpd
echo "<h1>Welcome to Apache Web Server on EC2</h1>" > /var/www/html/index.html
