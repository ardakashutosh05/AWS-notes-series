
📘 What is EC2 Instance Connect (Linux)?

EC2 Instance Connect allows secure SSH access to Linux EC2 instances.

Uses key pairs (.pem) for authentication.

Provides temporary access without storing SSH keys on the instance.

Works with Amazon Linux 2, Ubuntu, and other Linux AMIs.

🔹 Step-by-Step: Access Linux EC2 Instance
1. Launch a Linux EC2 Instance

AMI: Amazon Linux 2 / Ubuntu

Instance Type: t2.micro (free tier)

Security Group: allow SSH (port 22)

2. Download Key Pair

AWS generates .pem file when creating instance

Save it securely

3. Set Permissions on Key
chmod 400 mykey.pem

4. SSH into EC2
ssh -i mykey.pem ec2-user@<public-ip>


For Ubuntu AMI: username → ubuntu

5. Optional: EC2 Instance Connect via Console

Go to EC2 → Instance → Connect → EC2 Instance Connect → Connect

Browser-based SSH access (no terminal needed)

🔹 Example: SSH Command
ssh -i "mykey.pem" ec2-user@54.123.45.67


Connects securely to instance.

Run commands like sudo yum update -y, ls, top, etc.

🔹 Best Practices

Use key pairs securely; never share .pem publicly.

Restrict SSH access in security group (e.g., to your IP).

Use EC2 Instance Connect for temporary access instead of storing keys.

Enable CloudWatch logs to monitor SSH access.

Disable root login if using key pairs.


🎯 Interview Q&A

Q1: How do you connect to a Linux EC2 instance?
👉 Use SSH with .pem key file or EC2 Instance Connect.

Q2: Default username for Amazon Linux 2?
👉 ec2-user

Q3: Default username for Ubuntu AMI?
👉 ubuntu

Q4: What port is required for SSH access?
👉 TCP port 22

Q5: How can you improve SSH security?
👉 Restrict access by IP, use strong key pairs, disable password login, monitor CloudWatch logs.

Q6: Difference between EC2 Instance Connect and SSH via terminal?
👉 Instance Connect → browser-based, temporary; SSH via terminal → direct key-based access.
