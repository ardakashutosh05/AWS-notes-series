# 🔹 Amazon RDS – AWS Aurora Database

## 📖 Definition
- Amazon Aurora is a **relational database engine** built by AWS.
- Compatible with **MySQL** and **PostgreSQL**.
- Offers **high performance, scalability, and fault tolerance**.
- Storage auto-scales up to **128 TB**.
- 5x faster than MySQL and 3x faster than PostgreSQL.

---

## ⚙️ How Aurora Works
- Aurora **separates compute (instances)** from **storage layer**.
- Data is replicated **6 times across 3 AZs**.
- **Self-healing storage** repairs corrupt data automatically.
- Supports **continuous backup to S3**.

---

## 🛠️ Steps – Create First Aurora Instance
1. Go to **AWS Console → RDS → Create Database**.
2. Select **Amazon Aurora**.
3. Choose Edition:
   - Aurora MySQL-Compatible
   - Aurora PostgreSQL-Compatible
4. Enter DB cluster identifier.
5. Choose **Writer instance class**.
6. Configure networking (VPC, Subnet, Security Group).
7. Launch DB → Aurora cluster created.

---

## 🌍 Real Life Example
- **Ola/Uber ride-booking systems** → Aurora handles millions of ride requests with high reliability.
