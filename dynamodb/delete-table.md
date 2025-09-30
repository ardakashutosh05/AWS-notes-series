📘 Deleting a DynamoDB Table
🔹 1. Why Delete a Table?

Table is no longer needed.

Free up costs (RCU/WCU and storage).

Cleanup test or temporary tables after experimentation.

🔹 2. Deleting a Table
✅ CLI Example
aws dynamodb delete-table --table-name Orders


Operation is irreversible.

Deletes all data and indexes associated with the table.

Any pending requests fail after deletion starts.

🔹 3. Cleaning Up Associated Resources

Global/Local Secondary Indexes → automatically deleted with table.

Point-in-Time Recovery (PITR) → disabled automatically.

Backups → On-Demand backups remain; delete manually if needed.

Global Tables → must remove table from replication group first.

🔹 4. E-commerce Example

Table: Orders created for testing queries.

After test: delete-table Orders

Clean up: S3 exports (orders-export/) if not needed.

🔹 5. Best Practices

Take a backup before deleting production tables.

Ensure no applications are accessing the table.

Delete associated resources to avoid unnecessary costs.

Monitor CloudWatch metrics → confirm table deletion.

🎯 Interview Q&A

Q1: How do you delete a DynamoDB table?
👉 Use aws dynamodb delete-table --table-name <TableName> or delete via AWS Console.

Q2: Are indexes deleted automatically when table is deleted?
👉 Yes, both LSIs and GSIs are deleted automatically.

Q3: Does PITR get deleted when table is deleted?
👉 Yes, continuous backups (PITR) are disabled automatically.

Q4: Do On-Demand backups remain after table deletion?
👉 Yes, you must delete them manually if not needed.

Q5: Can you recover a table after deletion?
👉 Only if you have a backup (On-Demand or exported data).
