# 🔹 Amazon Aurora – Read Replica

## 📖 Definition
- Aurora supports **read replicas** to scale read operations.
- Replication is **asynchronous**, but faster than normal RDS due to **shared storage**.
- Up to **15 replicas** per Aurora cluster.

---

## ⚙️ How it Works
- Aurora uses **shared storage volume**.
- Writer updates → automatically available to all replicas.
- Replicas handle **read-only queries**.

---

## 🌍 Use Cases
- Offload heavy read queries.
- Analytics reporting without affecting primary.
- Geographically distributed applications.

---

## 🌍 Real Life Example
- **Netflix** → Metadata read traffic (movie names, thumbnails) served by replicas.
