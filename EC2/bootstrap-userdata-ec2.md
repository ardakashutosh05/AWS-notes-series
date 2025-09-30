📘 What is a Bootstrap Script / User Data?

User Data allows you to run scripts automatically when an EC2 instance launches.

Used for initial setup, software installation, and configuration.

Scripts are executed only once during the first boot of the instance.

Supports shell scripts (Linux) or PowerShell scripts (Windows).

🔹 Step-by-Step: Using User Data in Linux EC2

Launch EC2 Instance

Select AMI (Amazon Linux / Ubuntu)

Instance Type: t2.micro (free tier)

Enter User Data Script

In Advanced Details → User Data field, add script:

#!/bin/bash
yum update -y
yum install httpd -y
systemctl start httpd
systemctl enable httpd
echo "<h1>Hello from User Data EC2</h1>" > /var/www/html/index.html


Security Group: Allow HTTP (port 80)

Launch Instance

Script executes automatically on first boot

Verify

Open browser → http://<public-ip>

HTML page from User Data should appear

🔹 Step-by-Step: Using User Data in Windows EC2

Launch Windows EC2 instance

Enter PowerShell script in User Data:

<powershell>
Install-WindowsFeature -Name Web-Server -IncludeManagementTools
Write-Host "Hello from User Data Windows EC2" > C:\inetpub\wwwroot\index.html
</powershell>


Connect via RDP → check default IIS page

🔹 Best Practices

Use shebang (#!/bin/bash) for Linux scripts

Keep scripts idempotent → safe to re-run

Avoid sensitive info in plaintext → use Secrets Manager / Parameter Store

Combine User Data with CloudFormation / Terraform for automation

Check logs: /var/log/cloud-init-output.log (Linux) for script output

🎯 Interview Q&A

Q1: What is User Data in EC2?
👉 Scripts that run automatically during instance launch to configure software and settings.

Q2: When does User Data execute?
👉 Only during the first boot of the instance.

Q3: Can you run User Data again after launch?
👉 Not directly; you can rerun manually from /var/lib/cloud/ or by re-launching instance.

Q4: How to check if User Data ran successfully?
👉 Linux → /var/log/cloud-init-output.log, Windows → Event Viewer or script output.

Q5: Difference between User Data and manual setup?
👉 User Data → automated, reproducible, no manual SSH/RDP required.
