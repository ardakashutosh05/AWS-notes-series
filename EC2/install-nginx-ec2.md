📘 What is Nginx?

Nginx is a high-performance web server and reverse proxy.

Can serve static content, handle load balancing, and reverse proxy for applications.

Commonly used in web application deployments.

🔹 Step-by-Step: Install Nginx on EC2 (Linux)
1. Connect to EC2
ssh -i "mykey.pem" ec2-user@<public-ip>

2. Update Packages
sudo yum update -y          # Amazon Linux
sudo apt update -y          # Ubuntu

3. Install Nginx
sudo yum install nginx -y   # Amazon Linux
sudo apt install nginx -y   # Ubuntu

4. Start and Enable Nginx Service
sudo systemctl start nginx
sudo systemctl enable nginx

5. Configure Security Group

Allow HTTP (port 80) and HTTPS (port 443) inbound rules in Security Group.

6. Test Nginx

Open browser → http://<public-ip>

Default Nginx page should appear

🔹 Step 2: Deploy Sample HTML Application

Create HTML file:

sudo nano /usr/share/nginx/html/index.html


Add simple content:

<h1>Welcome to My EC2 Nginx Server</h1>
<p>Deployed successfully on AWS EC2!</p>


Save and exit → Refresh browser to see changes.

🔹 Best Practices

Keep Nginx updated for security.

Configure firewall / security group properly.

For production, use HTTPS (SSL/TLS) with Certbot or ACM.

Enable logging: access and error logs (/var/log/nginx/).

Automate deployment using User Data or CI/CD pipelines.

🎯 Interview Q&A

Q1: How do you install Nginx on EC2 Linux instance?
👉 Connect via SSH → update packages → install Nginx → start & enable service.

Q2: Where do you place HTML files for Nginx?
👉 /usr/share/nginx/html/

Q3: How to make Nginx start on instance reboot?
👉 sudo systemctl enable nginx

Q4: Which ports should be allowed for Nginx?
👉 HTTP → 80, HTTPS → 443

Q5: How to deploy a simple website on EC2 using Nginx?
👉 Place HTML/CSS/JS files in /usr/share/nginx/html/ and access via browser.
