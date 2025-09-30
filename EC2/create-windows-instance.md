📘 What is a Windows EC2 Instance?

EC2 instance running Microsoft Windows Server (2016, 2019, 2022).

Can be used for IIS web servers, .NET applications, Windows-based software.

Requires RDP access for management.

🔹 Step-by-Step: Create Windows EC2 Instance

Login to AWS Console → EC2 Dashboard → Launch Instances

Select AMI (Windows Server)

Example: Windows Server 2019 Base

Choose Instance Type

t2.micro → free tier eligible

Configure Instance Details

Network / Subnet → default VPC

Auto-assign Public IP → Yes

Add Storage

Default → 30 GB (Windows default)

Select EBS volume type

Add Tags (Optional)

Key: Name → Value: MyWindowsInstance

Configure Security Group

Allow RDP (3389) from your IP

Optional: HTTP/HTTPS if running IIS

Launch Instance

Create or select existing key pair → Download .pem

🔹 Step 2: Connect to Windows Instance

Go to EC2 Dashboard → Instances → Select Instance → Connect → RDP

Click Get Password → Upload .pem key → Decrypt password

Open Remote Desktop Connection → Enter public IP, username Administrator, decrypted password

🔹 Example

Public IP: 54.123.45.67

Username: Administrator

Password: (from key pair)

Connect via RDP client → access Windows desktop

🔹 Best Practices

Restrict RDP access to your IP only

Enable Windows Updates regularly

Install antivirus / endpoint protection

Use IAM roles for accessing AWS resources

Enable CloudWatch monitoring for instance health



🎯 Interview Q&A

Q1: How do you create a Windows EC2 instance?
👉 Select Windows AMI → choose instance type → configure network/storage → attach key pair → launch.

Q2: How do you connect to a Windows EC2 instance?
👉 Use RDP client with decrypted Administrator password from key pair.

Q3: Default username for Windows EC2?
👉 Administrator

Q4: Which port is required for Windows EC2 access?
👉 TCP port 3389 (RDP)

Q5: Best practices for Windows EC2?
👉 Restrict RDP, enable updates, install security software, use IAM roles, monitor via CloudWatch.
