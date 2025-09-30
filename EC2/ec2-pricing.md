📘 EC2 Pricing Overview

AWS EC2 pricing depends on how you use instances. Main factors:

Instance type & size (CPU, memory)

Region (different AWS regions have different prices)

Pricing model (On-Demand, Reserved, Spot, Savings Plan, Dedicated Host)

Storage, network, and additional services

🔹 1. On-Demand Instances

Pay hourly or per second for instance usage

No long-term commitment

Best for: unpredictable workloads, short-term apps

Example:

t2.micro in us-east-1 → $0.0116/hour

Interview Q&A:

Q: When to use On-Demand?
👉 For short-term or unpredictable workloads.

🔹 2. Reserved Instances (RI)

Commit 1 or 3 years to get a discounted rate

Payment options: All Upfront, Partial Upfront, No Upfront

Types: Standard RI (high discount), Convertible RI (flexible to change instance type)

Example:

t3.medium Standard RI → saves up to 40% vs On-Demand

Interview Q&A:

Q: Difference between Standard RI and Convertible RI?
👉 Standard → max discount, fixed instance type. Convertible → lower discount, can change instance type/family.

🔹 3. Spot Instances

Bid for unused EC2 capacity → up to 90% cheaper

Instances can be terminated if AWS needs capacity

Best for: batch processing, CI/CD, stateless apps

Interview Q&A:

Q: What is a Spot Instance?
👉 Cheap EC2 instance that can be interrupted; suitable for fault-tolerant workloads.

🔹 4. Savings Plans

Flexible commitment-based discount model

Pay less for usage across instance families & regions

Two types:

Compute Savings Plan → any EC2 instance usage

EC2 Instance Savings Plan → specific instance family in a region

Interview Q&A:

Q: Difference between RI and Savings Plan?
👉 RI → fixed instance type & region, Savings Plan → flexible usage for discount.

🔹 5. Dedicated Host

Physical server dedicated to your account only

Useful for licensing requirements or compliance

Can launch multiple instances on the host

Interview Q&A:

Q: Why use Dedicated Host?
👉 For compliance, license portability, and regulatory requirements.

🔹 Best Practices

Use On-Demand for unpredictable workloads

Use RI / Savings Plan for steady-state workloads

Use Spot Instances for cost savings in fault-tolerant apps

Combine pricing models for optimized cost and performance

Monitor usage via AWS Cost Explorer
