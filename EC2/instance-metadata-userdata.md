📘 What is EC2 Instance Metadata and User Data?

Instance Metadata: Data about your EC2 instance that can be accessed from within the instance.

Examples: Instance ID, public/private IP, AMI ID, region, security groups.

User Data: Custom data or scripts provided at launch to configure the instance automatically.

Access Method: Both can be accessed using HTTP request from inside the EC2 instance.

🔹 Accessing Instance Metadata (Linux)
# Instance ID
curl http://169.254.169.254/latest/meta-data/instance-id

# Public IP
curl http://169.254.169.254/latest/meta-data/public-ipv4

# AMI ID
curl http://169.254.169.254/latest/meta-data/ami-id

# Security groups
curl http://169.254.169.254/latest/meta-data/security-groups

🔹 Accessing User Data (Linux)
curl http://169.254.169.254/latest/user-data


Useful to check bootstrap scripts executed at launch.

Can include shell scripts, application configs, or setup commands.

🔹 Accessing Metadata/User Data (Windows)

Open PowerShell

# Instance ID
Invoke-RestMethod -Uri http://169.254.169.254/latest/meta-data/instance-id

# Public IP
Invoke-RestMethod -Uri http://169.254.169.254/latest/meta-data/public-ipv4

# User Data
Invoke-RestMethod -Uri http://169.254.169.254/latest/user-data

🔹 Best Practices

Avoid exposing metadata to public-facing applications (can leak sensitive info).

Use IAM roles instead of storing credentials in User Data.

Check cloud-init logs in Linux: /var/log/cloud-init-output.log to verify User Data execution.

Use metadata to automate instance configuration safely.

🎯 Interview Q&A

Q1: What is EC2 instance metadata?
👉 Data about an instance (ID, IP, AMI, security groups) accessible from within the instance.

Q2: What is User Data?
👉 Scripts or data provided at instance launch to configure it automatically.

Q3: How do you access instance metadata from Linux?
👉 curl http://169.254.169.254/latest/meta-data/<field>

Q4: How do you access User Data?
👉 curl http://169.254.169.254/latest/user-data

Q5: Why is metadata important?
👉 Useful for automation, monitoring, and dynamic configuration of EC2 instances.
