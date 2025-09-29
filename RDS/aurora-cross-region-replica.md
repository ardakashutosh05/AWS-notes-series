# 🔹 Amazon Aurora – Cross Region Read Replica

## 📖 Definition
- Aurora supports **replication across AWS Regions**.
- Used for **Disaster Recovery** and **Global Applications**.
- Replica in another region can be **promoted** to standalone DB.

---

## ⚙️ Use Cases
- **Disaster Recovery**: If primary region fails, promote replica in another region.
- **Global Scale**: Users in different continents read from local replica.

---

## 🛠️ Steps – Promote Read Replica
1. Go to **RDS Console → Aurora Cluster → Replicas**.
2. Select **Cross Region Replica** → Actions → Promote.
3. Replica becomes **independent DB cluster**.

---

## 🌍 Real Life Example
- **Amazon Prime**:
  - India → Mumbai region.
  - US → Virginia region.
  - If Mumbai fails, Virginia replica promoted to primary.
