📘 Amazon DynamoDB – Sort Key (Deep Dive with Example)
🔹 What is a Sort Key?

A Sort Key is the second part of a composite primary key (the first being the Partition Key).

DynamoDB allows multiple items to have the same Partition Key, but they must be uniquely identified using the Sort Key.

This enables one-to-many relationships within a single partition.

👉 Without Sort Key → Each Partition Key must be unique.
👉 With Sort Key → Multiple items can share the same Partition Key but have different Sort Keys.

🔹 Why is Sort Key Useful?

Efficient querying – Retrieve a subset of data within a Partition Key.

Range queries – Use operators (=, <, >, BETWEEN, begins_with) on Sort Keys.

Data modeling flexibility – Store related data together.

🔹 E-commerce Example: Orders Table
✅ Table Schema

Partition Key: CustomerID (String)

Sort Key: OrderDate (Number/Timestamp)

✅ Sample Data
CustomerID	OrderDate	OrderID	Product	Amount
CUST101	20250101	ORD001	Mobile	300$
CUST101	20250215	ORD002	Laptop	1200$
CUST101	20250301	ORD003	Headset	100$
CUST202	20250201	ORD004	Tablet	500$
✅ Query Examples

1. Get all orders for a customer:

aws dynamodb query \
  --table-name Orders \
  --key-condition-expression "CustomerID = :cust" \
  --expression-attribute-values '{":cust":{"S":"CUST101"}}'


2. Get orders for a customer between 1 Jan and 28 Feb 2025:

aws dynamodb query \
  --table-name Orders \
  --key-condition-expression "CustomerID = :cust AND OrderDate BETWEEN :start AND :end" \
  --expression-attribute-values '{
    ":cust":{"S":"CUST101"},
    ":start":{"N":"20250101"},
    ":end":{"N":"20250228"}
  }'


3. Get the most recent order (latest Sort Key):

Use ScanIndexForward = false (descending order).

aws dynamodb query \
  --table-name Orders \
  --key-condition-expression "CustomerID = :cust" \
  --expression-attribute-values '{":cust":{"S":"CUST101"}}' \
  --scan-index-forward false \
  --limit 1

🔹 Benefits of Sort Key in E-commerce

Customers can have multiple orders (1-to-many relationship).

We can efficiently query:

Last order of a customer.

All orders in a specific month.

Orders above a certain date.

This avoids full table scans and improves performance + cost efficiency.

🔹 Interview Questions

Q1. Why do we use a Sort Key in DynamoDB?
👉 To allow multiple items with the same Partition Key and support range queries within that partition.

Q2. Give an e-commerce use case of Sort Key.
👉 CustomerID as Partition Key, OrderDate as Sort Key → fetch all orders of a customer, or latest order.

Q3. Can a table have more than one Sort Key?
👉 No, only one Sort Key per table. But you can define Global Secondary Indexes (GSIs) for additional query patterns.

Q4. What operators can be used with Sort Key in queries?
👉 =, <, <=, >, >=, BETWEEN, begins_with.
