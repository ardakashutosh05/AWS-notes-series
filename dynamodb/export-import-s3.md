📘 Exporting and Importing DynamoDB Data to/from S3
🔹 1. Why Export/Import?

Export to S3 → Backup data, analytics, or share with other systems.

Import from S3 → Load bulk data into DynamoDB efficiently.

Helps integrate DynamoDB with data lakes, ETL, or analytics pipelines.

🔹 2. Exporting Data from DynamoDB to S3
✅ Features

Exports entire table or a point-in-time snapshot.

No downtime for the table.

Stored in Parquet format (efficient for analytics).

✅ CLI Example: Export Table to S3
aws dynamodb export-table-to-point-in-time \
    --table-arn arn:aws:dynamodb:us-east-1:123456789012:table/Orders \
    --s3-bucket my-dynamodb-backup \
    --s3-prefix orders-export \
    --export-time 2025-09-25T10:00:00Z


--export-time optional → default is latest data.

Creates export in S3 bucket in a folder (s3-prefix).

🔹 3. Importing Data from S3 to DynamoDB
✅ Features

Bulk load data from S3 Parquet or JSON files.

Efficient → avoids individual PutItem operations.

✅ CLI Example: Import Table from S3
aws dynamodb import-table \
    --s3-bucket-source my-dynamodb-backup \
    --s3-bucket-source-prefix orders-export/ \
    --table-name OrdersRestore


Creates a new table (OrdersRestore).

Source must be in valid DynamoDB export format.

🔹 4. E-commerce Example

Table: Orders

Export all orders to S3 → orders-export/2025-09-25

Import to a new table in another region → OrdersRestore

Enables analytics or disaster recovery.

🔹 5. Best Practices

Use point-in-time export for backups before major changes.

Keep S3 bucket encrypted (AES-256/KMS).

Automate exports using AWS Backup or Lambda.

Monitor import/export progress via CloudWatch Events.

Limit table write throughput during import → avoid throttling.

🎯 Interview Q&A

Q1: Why would you export DynamoDB data to S3?
👉 For backup, analytics, or integration with other systems.

Q2: Does exporting affect the live table?
👉 No, export is non-disruptive.

Q3: Can you import data into an existing table?
👉 No, imports always create a new table.

Q4: What formats are used in DynamoDB export?
👉 Parquet or DynamoDB JSON.

Q5: Can you schedule automated exports to S3?
👉 Yes, via AWS Backup, Lambda, or Step Functions.
