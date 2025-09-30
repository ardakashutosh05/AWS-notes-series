
1️⃣ Create First EC2 Instance
🔹 Steps (Linux/Windows)

Go to EC2 Dashboard → Launch Instances

Choose AMI (Amazon Linux / Ubuntu / Windows Server)

Select Instance Type (t2.micro for free tier)

Configure network & subnet

Add storage (EBS)

Add tags (optional)

Configure security group (allow SSH/HTTP/RDP)

Review & Launch, choose key pair

🔹 Interview Q&A

Q: What is an EC2 Instance?
👉 Virtual server in AWS cloud, scalable and secure.

Q: Difference between AMI and Instance Type?
👉 AMI → OS and pre-installed software. Instance Type → CPU, memory, network capacity.

2️⃣ Access EC2 Instance
🔹 From Windows Machine (SSH)

Download .pem key

Open PuTTY → convert .pem to .ppk

Use SSH to connect:

ssh -i "key.pem" ec2-user@<public-ip>

🔹 From Linux Machine
chmod 400 key.pem
ssh -i key.pem ec2-user@<public-ip>

🔹 Interview Q&A

Q: Default username for Amazon Linux AMI?
👉 ec2-user

Q: How to connect Windows EC2 via RDP?
👉 Download password from key pair → use Remote Desktop Client.

3️⃣ Install Nginx / Deploy Sample App

Update packages: sudo yum update -y

Install Nginx: sudo yum install nginx -y

Start service: sudo systemctl start nginx

Enable on boot: sudo systemctl enable nginx

Test via browser → http://<public-ip>

🔹 Interview Q&A

Q: How to check Nginx status?
👉 systemctl status nginx

Q: How to deploy simple HTML app?
👉 Copy files to /usr/share/nginx/html/

4️⃣ Bootstrap / User Data Script

Used to run scripts at instance launch automatically.

Example:

#!/bin/bash
yum update -y
yum install httpd -y
systemctl start httpd
systemctl enable httpd
echo "Hello from EC2" > /var/www/html/index.html

🔹 Interview Q&A

Q: Difference between User Data and manual config?
👉 User Data runs automatically at first launch; manual config requires SSH.

5️⃣ Security Groups

Acts as a virtual firewall for instances.

Rules: allow inbound/outbound traffic based on port, protocol, IP

Example: HTTP → port 80, SSH → port 22

🔹 Interview Q&A

Q: Difference between Security Group and NACL?
👉 SG → instance-level firewall, stateful. NACL → subnet-level firewall, stateless.

6️⃣ EC2 Instance Types

Categories: General Purpose, Compute Optimized, Memory Optimized, Storage Optimized, GPU

Example: t2.micro → 1 vCPU, 1GB RAM (free tier)

🔹 Interview Q&A

Q: How to choose instance type?
👉 Based on CPU, memory, storage, network requirements.

7️⃣ AWS Pricing & Cost Optimization

Pricing Models: On-Demand, Reserved, Spot, Savings Plan, Dedicated Host

Spot → cheaper but can be interrupted.

Reserved → save costs with 1-3 year commitment.

🔹 Interview Q&A

Q: Difference between On-Demand and Reserved Instances?
👉 On-Demand → pay per hour, no commitment. Reserved → upfront cost, lower hourly rate.

8️⃣ Windows Instance Setup & Access

Launch Windows instance → get password from key pair

Connect via RDP client using public IP

🔹 Interview Q&A

Q: Default username for Windows EC2?
👉 Administrator

9️⃣ Instance Metadata & User Data

Metadata URL: http://169.254.169.254/latest/meta-data/

Contains instance info like ID, type, AMI, security groups

🔹 Interview Q&A

Q: How to access instance metadata?
👉 Curl command: curl http://169.254.169.254/latest/meta-data/

🔟 Elastic / Static IP (EIP)
🔹 Attach

Allocate Elastic IP → EC2 Dashboard → Elastic IPs

Associate with instance → ensures fixed public IP

🔹 Detach / Release

Release IP when no longer needed → reduces cost

🔹 Interview Q&A

Q: Difference between public IP and Elastic IP?
👉 Public IP → changes on stop/start. Elastic IP → static, persistent.
