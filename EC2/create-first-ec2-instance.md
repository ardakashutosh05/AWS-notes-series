📘 What is an EC2 Instance?

EC2 (Elastic Compute Cloud) → virtual server in AWS cloud.

Can run Linux, Windows, or custom AMIs.

Key features: scalable, secure, pay-as-you-go.

🔹 Step-by-Step: Create First EC2 Instance

Login to AWS Console → EC2 Dashboard → Launch Instance

Select AMI:

Amazon Linux 2025

Ubuntu Server

Windows Server

Choose Instance Type:

t2.micro (free tier) → 1 vCPU, 1GB RAM

Configure Instance Details:

Select VPC / Subnet

Auto-assign Public IP: Yes

Add Storage:

Default EBS → 8GB

Encryption optional

Add Tags (optional):

Key: Name → Value: MyFirstEC2

Configure Security Group:

Allow SSH (22) for Linux

Allow RDP (3389) for Windows

Allow HTTP (80) for web access

Review & Launch → Select Key Pair → Launch

🔹 Connect to Instance

Linux Instance:

chmod 400 mykey.pem
ssh -i mykey.pem ec2-user@<public-ip>


Windows Instance:

Decrypt password using key pair

Connect via Remote Desktop (RDP) using public IP

🔹 Best Practices

Use key pairs for secure access.

Choose appropriate instance type for workload.

Use security groups to restrict access.

Tag instances for easy management.

🎯 Interview Q&A



Q1: What is an EC2 instance?
👉 A virtual server in AWS that provides scalable compute capacity.

Q2: What is the difference between AMI and Instance Type?
👉 AMI → OS + software; Instance Type → CPU, memory, network capacity.

Q3: How to connect to a Linux EC2 instance?
👉 Use SSH with .pem key file.

Q4: How to connect to Windows EC2 instance?
👉 Use RDP client with password decrypted from key pair.
