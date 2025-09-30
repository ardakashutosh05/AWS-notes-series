📘 What are DynamoDB Global Tables?

Global Tables allow multi-region, fully replicated tables.

Provides active-active replication → multiple regions can read/write simultaneously.

Ensures low-latency access globally and disaster recovery.

Conflict resolution: Last Writer Wins (based on timestamp).

🔹 Key Features

Multi-region replication → updates automatically propagate across regions.

Active-Active model → read/write operations in all regions.

Disaster recovery → table can failover to another region.

Automatic scaling → inherits provisioned or on-demand capacity settings.

🏪 E-commerce Example

Table: Orders

Regions: us-east-1, ap-south-1

Customers in US and India can write orders simultaneously.

All orders automatically appear in both regions.

✅ CLI Example: Create Global Table
aws dynamodb create-global-table \
    --global-table-name OrdersGlobal \
    --replication-group RegionName=us-east-1 RegionName=ap-south-1

✅ Use Case

Global customer base → low-latency access.

High availability → region fails, app continues in other regions.

Analytics across regions → replicated data available in multiple regions.

🔹 Best Practices

Choose regions close to your users for low latency.

Monitor replication lag using CloudWatch.

Understand write conflicts and timestamp precedence.

Avoid excessive GSIs on global tables → can increase replication complexity.

🎯 Interview Q&A

Q1: What are DynamoDB Global Tables?
👉 Multi-region replicated tables allowing active-active read/write access globally.

Q2: How does conflict resolution work in Global Tables?
👉 Last Writer Wins → the item with the latest timestamp overwrites the previous.

Q3: Can you create Global Tables from existing tables?
👉 Yes, existing tables can be added to a replication group.

Q4: Why use Global Tables in DynamoDB?
👉 Low-latency global access, disaster recovery, high availability.

Q5: How many regions can a Global Table replicate to?
👉 Up to five regions per table (as per AWS limits).
