📘 What is a Security Group?

Security Group (SG) = virtual firewall for EC2 instances.

Controls inbound and outbound traffic at the instance level.

Stateful → if you allow inbound traffic, the response is automatically allowed outbound.

Can be applied to one or multiple instances.

🔹 Key Features

Stateful: Return traffic automatically allowed.

Allow rules only: No deny rules; deny by default.

Multiple SGs per instance: Up to 5 per instance (soft limit).

Dynamic rules: Changes take effect immediately.

🔹 Step-by-Step: Create Security Group

Go to EC2 Dashboard → Security Groups → Create Security Group

Name & Description: e.g., web-sg

VPC Selection: Choose VPC

Inbound Rules:

SSH (22) → My IP

HTTP (80) → 0.0.0.0/0

HTTPS (443) → 0.0.0.0/0

Outbound Rules: By default → All traffic allowed

Attach Security Group

During instance launch or modify an existing instance

🔹 Example
Type	Protocol	Port Range	Source
SSH	TCP	22	203.0.113.25/32
HTTP	TCP	80	0.0.0.0/0
HTTPS	TCP	443	0.0.0.0/0
🔹 Best Practices

Restrict SSH/RDP access to specific IPs

Use separate SGs for web, app, database layers

Avoid using 0.0.0.0/0 for sensitive ports in production

Tag security groups for easy management

Monitor traffic with VPC Flow Logs

🎯 Interview Q&A

Q1: What is a Security Group?
👉 Virtual firewall controlling inbound/outbound traffic for EC2 instances.

Q2: Is a Security Group stateful or stateless?
👉 Stateful – response traffic is automatically allowed.

Q3: Difference between Security Group and NACL?

SG → instance-level, stateful, allows only allow rules

NACL → subnet-level, stateless, supports allow & deny rules

Q4: Can you modify Security Group rules for a running instance?
👉 Yes, changes take effect immediately.

Q5: How many Security Groups can you attach per instance?
👉 Default soft limit: 5 (can request increase)

Q6: Best practices for Security Groups?
👉 Restrict SSH/RDP, separate SGs per layer, avoid 0.0.0.0/0 for sensitive ports, monitor with Flow Logs.
