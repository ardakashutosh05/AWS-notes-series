📘 Amazon DynamoDB – Local Secondary Index (LSI)
🔹 1. What is a Local Secondary Index (LSI)?

An index that allows queries on an alternative Sort Key, while keeping the same Partition Key as the base table.

Must be defined at the time of table creation (cannot add later).

Supports up to 5 LSIs per table.

Enables different query patterns within the same partition.

👉 Think of LSI as another way to sort/query items within a partition.

🔹 2. Key Rules of LSI

Partition Key = Same as base table

Sort Key = Different attribute (chosen at table creation)

Maximum 5 LSIs per table

LSIs consume base table RCUs/WCUs (not separate capacity)

Support strongly consistent reads (unlike GSI)

🔹 3. E-commerce Example – Orders Table
Base Table Schema

Partition Key: CustomerID

Sort Key: OrderDate

Local Secondary Index Schema

Partition Key: CustomerID (same)

Sort Key: Amount (instead of OrderDate)

✅ Sample Data
CustomerID	OrderDate	OrderID	Product	Amount
CUST101	2025-01-01	ORD001	Mobile	300$
CUST101	2025-02-15	ORD002	Laptop	1200$
CUST101	2025-03-01	ORD003	Headset	100$
✅ Query Examples

1. Fetch orders by CustomerID sorted by Amount (via LSI):

aws dynamodb query \
  --table-name Orders \
  --index-name AmountIndex \
  --key-condition-expression "CustomerID = :cust" \
  --expression-attribute-values '{":cust":{"S":"CUST101"}}'


2. Fetch all orders for CUST101 where Amount > 500 (via LSI):

aws dynamodb query \
  --table-name Orders \
  --index-name AmountIndex \
  --key-condition-expression "CustomerID = :cust AND Amount > :amt" \
  --expression-attribute-values '{
    ":cust":{"S":"CUST101"},
    ":amt":{"N":"500"}
  }'

🔹 4. Benefits of LSI

Enables multiple sort key options for the same data.

Supports strongly consistent reads.

Allows filtering/querying on different dimensions without creating a new table.

🔹 5. Limitations of LSI

Must be created with the table (cannot add later).

Maximum 5 LSIs per table.

Shares provisioned throughput with the base table.

Increases storage size (copies data).

🔹 6. Best Practices

Define LSIs only for required access patterns.

Use LSIs when you know queries will always use the same partition key.

Avoid unnecessary LSIs to save cost and complexity.

Prefer GSI if you need a different partition key.

🔹 7. Interview Q&A

Q1. What is the difference between LSI and GSI?
👉 LSI uses the same Partition Key but a different Sort Key.
👉 GSI allows a completely different Partition Key + Sort Key.

Q2. How many LSIs can you create per table?
👉 Maximum 5 LSIs per table.

Q3. Can you add LSI after table creation?
👉 No, LSIs must be defined when the table is created.

Q4. Does LSI support strongly consistent reads?
👉 Yes, unlike GSIs which only support eventual consistency.

Q5. In what scenarios would you prefer an LSI?
👉 When you need to query the same partition but with a different sort key (e.g., by Amount instead of OrderDate).
