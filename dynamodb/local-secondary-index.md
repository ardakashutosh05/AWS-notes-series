📘 What is a Local Secondary Index (LSI)?

A Local Secondary Index (LSI) is an alternate sort key on the same partition key of a DynamoDB table.

It allows you to query the same partition (same HASH key) using different sorting attributes.

Maximum 5 LSIs per table (at table creation only – can’t add later).

Uses strongly consistent reads (unlike GSI which supports eventual consistency only).

🏪 E-commerce Example
Base Table: Orders

Partition Key: CustomerID

Sort Key: OrderID

Now, suppose we want to query customer’s orders by OrderDate instead of OrderID.
We can’t create a new table every time → we use LSI.

LSI Example:

LSI Name: OrderDateIndex

Partition Key: CustomerID (same as base table)

Sort Key: OrderDate

📊 Data Example
CustomerID	OrderID	OrderDate	Amount	Status
CUST001	ORD001	2025-09-10	500	Shipped
CUST001	ORD002	2025-09-15	1200	Pending
CUST002	ORD003	2025-09-12	800	Shipped
✅ Queries Possible with LSI

Find all orders of CUST001 sorted by date

Partition Key = "CUST001"
Sort Key (OrderDate) between "2025-09-10" and "2025-09-20"


Get latest order of a customer

Use ScanIndexForward = false → returns most recent order first.

Filter customer’s orders by status

Query by CustomerID, then filter Status.

⚡ LSI vs GSI
Feature	LSI	GSI
Partition Key	Same as base table	Different possible
Sort Key	Different from base table	Different possible
Creation Time	Only at table creation	Anytime
Consistency	Supports strongly consistent reads	Only eventual consistency
Use Case	Query within same partition, with alternate sort key	Query across different partitions
🛠 Best Practices

Define LSIs carefully at table creation (cannot add later).

Use LSIs when you need different query patterns for same partition key.

Keep in mind LSIs consume WCU/RCU of base table.

Do not overuse LSIs (max 5) → plan schema design first.

🎯 Interview Q&A

Q1: What is LSI in DynamoDB?
👉 A Local Secondary Index is an index with the same partition key but a different sort key, allowing alternate query patterns within a partition.

Q2: Can we add LSI after table creation?
👉 No, LSIs must be defined at the time of table creation.

Q3: How many LSIs can a table have?
👉 Up to 5 LSIs per table.

Q4: What’s the difference between LSI and GSI?
👉 LSI → same partition key, different sort key, strong consistency.
👉 GSI → different partition key, eventual consistency only.

Q5: Give an example of LSI in e-commerce.
👉 Table: Orders with partition key CustomerID and sort key OrderID.
LSI: CustomerID + OrderDate → helps query orders by date.
