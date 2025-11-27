# EC2 Web Server Project

This project demonstrates the deployment of a simple public web application using **AWS EC2**, **Amazon Linux 2**, and **Apache HTTP Server**.  
It showcases fundamental **DevOps/DevSecOps skills** and is designed as a portfolio project.

---

## Project Overview

- Launch an **EC2 instance** (Amazon Linux 2, t3.micro) in AWS
- Configure **security groups** for SSH (port 22) and HTTP (port 80)
- Install and configure **Apache HTTP Server**
- Create a simple web page accessible via a **public IP**
- Apply basic **DevSecOps best practices** (secure SSH, software updates, firewall)

---

## Architecture Diagram

            ┌──────────────────────────────┐
            │          Internet            │
            └─────────────┬────────────────┘
                          │ HTTP (80)
                          ▼
                ┌─────────────────────┐
                │     Security Group  │
                │  (Allow 22 & 80)    │
                └───────────┬─────────┘
                            │
                            ▼
                ┌─────────────────────┐
                │      EC2 Instance   │
                │   Amazon Linux 2    │
                │ Running Apache HTTPD│
                └───────────┬─────────┘
                            │
                            ▼
                 /var/www/html/index.html
                         (Web App)


---

## Deployment Steps

1. **Launch EC2 instance**
   - Region: London (eu-west-2)
   - Instance type: t3.micro (free tier)
   - Key pair: create/download
   - Security group: SSH from your IP, HTTP from anywhere

2. **Connect to EC2**
   ```bash
   # Using EC2 Instance Connect
   EC2 → Instances → Connect → EC2 Instance Connect → Connect

3. Install Apache

	sudo yum update -y
	sudo yum install -y httpd
	sudo systemctl start httpd
	sudo systemctl enable httpd


4. Create sample web page

echo "<h1>Hello from Chynna's EC2 Web App</h1>" | sudo tee /var/www/html/index.html


5. Verify locally

curl http://localhost


6. View in browser

http://<Public-IP-of-EC2>
