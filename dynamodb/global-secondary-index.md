global-secondary-index.md
📘 What is a Global Secondary Index (GSI)?

A Global Secondary Index (GSI) is an index with a different Partition Key and optionally a different Sort Key from the base table.

Can be created anytime, even after table creation.

Supports eventually consistent reads (strongly consistent reads optional in certain SDKs).

Max 20 GSIs per table.

Helps query data using attributes that are not primary key of the base table.

🏪 E-commerce Example
Base Table: Orders

Partition Key: CustomerID

Sort Key: OrderDate

GSI Example: Query orders by ProductID

GSI Name: ProductIndex

Partition Key: ProductID

Sort Key: OrderDate

Now you can query all customers who bought a specific product, which isn’t possible with base table keys.

📊 Sample Data
CustomerID	OrderID	ProductID	OrderDate	Amount
CUST001	ORD001	PROD101	2025-09-10	500
CUST001	ORD002	PROD102	2025-09-15	1200
CUST002	ORD003	PROD101	2025-09-12	800
✅ Queries Using GSI

Get all orders of Product PROD101

aws dynamodb query \
  --table-name Orders \
  --index-name ProductIndex \
  --key-condition-expression "ProductID = :pid" \
  --expression-attribute-values '{":pid":{"S":"PROD101"}}'


Get all orders of Product PROD101 sorted by OrderDate

Use ScanIndexForward = true/false for ascending/descending.

⚡ GSI vs LSI
Feature	GSI	LSI
Partition Key	Can be different	Must be same as base table
Sort Key	Can be different	Must be different from base table
Creation Time	Anytime	Only at table creation
Consistency	Eventually consistent (strong optional)	Strongly consistent
Use Case	Query across partitions	Query within same partition with alternate sort key
🛠 Best Practices

Create GSIs only for required access patterns.

Avoid too many GSIs → each adds storage and RCU/WCU cost.

Monitor GSI usage metrics to optimize throughput.

Use sparse indexes for queries that filter only certain items.

🎯 Interview Q&A

Q1: What is a GSI in DynamoDB?
👉 A Global Secondary Index is an index with a different Partition Key and optional Sort Key that allows querying data using non-primary key attributes.

Q2: Can you create a GSI after table creation?
👉 Yes, anytime.

Q3: Difference between GSI and LSI?
👉 GSI → different partition key, eventual consistency; LSI → same partition key, strong consistency.

Q4: Maximum GSIs per table?
👉 20 GSIs per table.

Q5: Example of GSI in e-commerce.
👉 Query orders by ProductID across all customers (Partition Key = ProductID) using a GSI.

Q6: Does GSI consume RCU/WCU of base table?
👉 No, GSIs have separate provisioned capacity or share On-Demand billing.
