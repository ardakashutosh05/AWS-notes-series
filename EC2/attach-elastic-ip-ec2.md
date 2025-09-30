📘 What is an Elastic IP?

Elastic IP (EIP) = static, public IPv4 address provided by AWS.

Can be associated with any EC2 instance in your account.

Unlike public IPs, Elastic IPs do not change when an instance is stopped/restarted.

Useful for web servers, DNS, and consistent access.

🔹 Step-by-Step: Attach Elastic IP to EC2
1. Allocate an Elastic IP

Go to EC2 Dashboard → Network & Security → Elastic IPs → Allocate Elastic IP

Click Allocate Elastic IP address → AWS allocates an IP

2. Associate Elastic IP to EC2

Select Elastic IP → Actions → Associate Elastic IP

Choose:

Instance → Select your EC2 instance

Private IP → Default private IP of the instance

Click Associate

3. Verify

Go to Instances → Public IPv4 address → should match Elastic IP

Test in browser or ping: ping <Elastic-IP>

🔹 Detach Elastic IP (Optional)

Select EIP → Actions → Disassociate Elastic IP

Can reassociate to another instance later

🔹 Best Practices

Use Elastic IP only when needed (AWS charges for unused EIPs).

Avoid assigning EIP to multiple instances simultaneously.

Use DNS with EIP for reliable application endpoints.

Monitor IP usage to control costs.

🎯 Interview Q&A

Q1: What is an Elastic IP?
👉 A static public IP address for EC2 that does not change across reboots.

Q2: Difference between public IP and Elastic IP?

Public IP → changes if instance stops/starts

Elastic IP → static, persists across instance stop/start

Q3: How to associate an Elastic IP to EC2?
👉 Allocate EIP → Actions → Associate → Choose instance and private IP.

Q4: Can you use an Elastic IP with multiple instances?
👉 No, one EIP can be associated with only one instance at a time.

Q5: Will AWS charge for Elastic IP?
👉 Yes, if allocated but not associated with a running instance.
