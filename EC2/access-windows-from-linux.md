📘 Overview

Accessing a Windows EC2 instance from a Linux machine requires RDP client tools.

Linux does not have a native RDP GUI like Windows, so we use rdesktop, Remmina, or xfreerdp.

Key pair is used to decrypt the Administrator password for login.

🔹 Step-by-Step: Access Windows EC2 from Linux
1. Prerequisites

Linux system (Ubuntu, CentOS, Amazon Linux)

RDP client installed:

# Ubuntu
sudo apt install remmina freerdp2-x11 -y

# CentOS / Amazon Linux
sudo yum install freerdp -y

2. Decrypt Windows Password

Go to AWS EC2 Console → Instances → Select Windows Instance → Connect → RDP

Click Get Password

Upload your .pem key → Decrypt password

3. Connect Using RDP Client
Option 1: Remmina GUI

Open Remmina → RDP

Enter Public IP

Username: Administrator

Password: decrypted key

Connect

Option 2: CLI using xfreerdp
xfreerdp /v:<Public-IP> /u:Administrator /p:<Password>

🔹 Example

Public IP: 54.123.45.67

Username: Administrator

Password: decrypted via AWS console

Connect with Remmina or xfreerdp

🔹 Best Practices

Restrict RDP access in Security Group to your IP

Use strong, complex passwords

Enable NLA (Network Level Authentication)

Monitor login attempts with CloudWatch logs

Consider bastion host or VPN for secure access

🎯 Interview Q&A

Q1: How do you access Windows EC2 from Linux?
👉 Use RDP client (Remmina, xfreerdp, rdesktop) with decrypted Administrator password.

Q2: Which Linux RDP clients are commonly used?
👉 Remmina, xfreerdp, rdesktop.

Q3: How do you decrypt the Windows password for RDP?
👉 Go to EC2 console → Connect → Get Password → Upload key pair .pem → Decrypt.

Q4: What security precautions should you take?
👉 Restrict RDP access by IP, enable NLA, use strong password, monitor via CloudWatch, consider bastion host.

Q5: Can you connect without decrypting the password?
👉 No, the Administrator password must be decrypted using the key pair.
