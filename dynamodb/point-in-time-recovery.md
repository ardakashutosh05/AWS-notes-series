📘 What is Point-in-Time Recovery (PITR)?

PITR is a continuous backup feature in DynamoDB.

Allows you to restore your table to any second in the past 35 days.

Protects against accidental writes/deletes or corruption.

PITR is enabled per table and works automatically once turned on.

🔹 Types of Backups in DynamoDB
Backup Type	Description
On-Demand Backup	Manual snapshot, retained until deleted, useful for scheduled backups before major changes.
PITR	Continuous backup, rolling 35-day window, automatic, restores to any second.
🏪 E-commerce Example

Table: Orders

Accident: A customer’s orders for the last 2 days were accidentally deleted.

Solution: Restore the table to specific point before deletion using PITR.

✅ CLI Example: Enable PITR
aws dynamodb update-continuous-backups \
    --table-name Orders \
    --point-in-time-recovery-specification PointInTimeRecoveryEnabled=true

✅ Restore Table to Specific Time
aws dynamodb restore-table-to-point-in-time \
    --source-table-name Orders \
    --target-table-name Orders_Restore \
    --restore-date-time 2025-09-25T10:00:00Z


Note: Restoration creates a new table; you cannot overwrite the existing table.

🔹 Benefits of PITR

Protects against accidental deletes or updates.

Provides fine-grained recovery (any second in last 35 days).

Ensures minimal downtime and data loss.

🔹 Best Practices

Enable PITR for all production tables.

Combine PITR + On-Demand Backup for critical changes.

Monitor table backups and restore regularly to test DR (Disaster Recovery) process.

Understand billing: PITR is charged per GB of data.

🎯 Interview Q&A

Q1: What is PITR in DynamoDB?
👉 Continuous backup that allows restoring table to any second in the past 35 days.

Q2: How is PITR different from On-Demand Backup?
👉 PITR = continuous, automatic, rolling 35-day window; On-Demand = manual snapshot.

Q3: Can PITR overwrite the existing table?
👉 No, it restores to a new table.

Q4: When would you use PITR?
👉 For production tables to recover from accidental deletion, corruption, or unwanted updates.

Q5: What’s the maximum recovery window for PITR?
👉 35 days.
