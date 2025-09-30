📘 What is EC2 Instance Connect (Windows)?

EC2 Instance Connect allows secure access to EC2 instances.

For Windows instances, you connect using Remote Desktop Protocol (RDP).

Requires a key pair to decrypt the password for login.

Provides temporary password for secure access.

🔹 Step-by-Step: Access Windows EC2 Instance

Launch a Windows EC2 instance

AMI: Windows Server 2019 / 2022

Instance Type: t2.micro (free tier)

Ensure Security Group allows RDP (port 3389)

Source: Your IP / 0.0.0.0/0 (not recommended for production)

Get the Administrator Password

Go to EC2 Console → Instances → Select Instance → Connect → RDP

Click Get Password → Upload your .pem key → Decrypt password

Connect Using Remote Desktop

Open Remote Desktop Connection (Windows: mstsc)

Enter Public IP of instance

Username: Administrator

Password: decrypted from key pair

Optional: Save credentials for future sessions

🔹 Example: RDP Connection

Public IP: 54.123.45.67

Username: Administrator

Password: (decrypted using key pair)

Open mstsc → 54.123.45.67 → Connect

🔹 Best Practices

Restrict RDP access to specific IPs only.

Use strong passwords and key pairs.

Enable Network Level Authentication (NLA).

Regularly update Windows security patches.

Consider AWS Systems Manager Session Manager for secure access without opening port 3389.

🎯 Interview Q&A

Q1: How do you access a Windows EC2 instance?
👉 Use RDP client with public IP and Administrator password decrypted from key pair.

Q2: What port is required for Windows EC2 access?
👉 TCP port 3389 (RDP).

Q3: Can you access Windows EC2 without a key pair?
👉 No, key pair is required to decrypt the initial Administrator password.

Q4: How to improve Windows EC2 access security?
👉 Restrict RDP to trusted IPs, enable NLA, or use AWS Systems Manager Session Manager.

Q5: Difference between EC2 Instance Connect and RDP for Windows?
👉 EC2 Instance Connect is AWS’s secure access method, but for Windows, RDP is standard.
