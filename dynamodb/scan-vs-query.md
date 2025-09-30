📘 Amazon DynamoDB – Scan vs Query
🔹 1. What is a Query?

A Query operation retrieves items using the Partition Key (and optionally Sort Key conditions).

It is targeted – only looks at items matching the key condition.

Efficient (uses indexes internally).

👉 Example: “Get all orders of CustomerID = CUST101 between Jan and March.”

🔹 2. What is a Scan?

A Scan operation examines every item in the table (or index).

It then filters out the items that do not match the filter expression.

Costly for large tables (reads all data even if only a few items match).

👉 Example: “Find all orders where Amount > 100$ (without knowing CustomerID).”

🔹 3. Architecture Comparison
Feature	Query 🚀 (Efficient)	Scan 🐢 (Expensive)
Access Pattern	Uses Partition Key (and Sort Key)	Scans entire table/index
Performance	Fast (O(1) lookup in partition)	Slow (O(n) full scan)
RCU Consumption	Reads only matching items	Reads all items in table
Use Case	Known key lookups, range queries	Analytics, debugging, unknown keys
Filter Expression	Optional (after key lookup)	Mandatory (to reduce data returned)
🔹 4. E-commerce Example
Table: Orders

Partition Key: CustomerID

Sort Key: OrderDate

✅ Query Example – Fetch orders of a customer
aws dynamodb query \
  --table-name Orders \
  --key-condition-expression "CustomerID = :cust" \
  --expression-attribute-values '{":cust":{"S":"CUST101"}}'


👉 Returns only orders of CustomerID = CUST101.

✅ Scan Example – Find all orders above $1000
aws dynamodb scan \
  --table-name Orders \
  --filter-expression "Amount > :amt" \
  --expression-attribute-values '{":amt":{"N":"1000"}}'


👉 Scans entire table, then filters out orders below 1000.

🔹 5. Best Practices

Prefer Query over Scan (cost & performance).

If Scan is unavoidable:

Use parallel scans for speed.

Apply ProjectionExpression to return only needed attributes.

Use filters to reduce response size.

For analytics → Export data to S3 + Athena instead of scanning DynamoDB.

🔹 6. Interview Q&A

Q1. What is the main difference between Query and Scan in DynamoDB?
👉 Query retrieves data using Partition Key (efficient), while Scan examines entire table (expensive).

Q2. When should you use Scan instead of Query?
👉 When you don’t know the Partition Key, e.g., “find all customers who ordered product X”.

Q3. Does Scan read the entire table even if filters are applied?
👉 Yes. Filters are applied after reading all items, so RCUs are still consumed.

Q4. How can you optimize Scan operations?
👉 Use parallel scans, ProjectionExpression, filters, or move data to S3 for analytics.

Q5. Which operation is recommended for real-time APIs?
👉 Query (predictable and fast).
