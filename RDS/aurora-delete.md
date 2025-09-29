# 🔹 Amazon Aurora – Delete Database & Read Replica

## 🛠️ Delete Aurora Database
1. AWS Console → RDS → Databases → Select Aurora Cluster.
2. Actions → Delete.
3. Choose:
   - Final snapshot (optional).
   - Retain backups (optional).
4. Confirm deletion.

---

## 🛠️ Delete Aurora Read Replica
1. RDS Console → Aurora Cluster → Instances.
2. Select Read Replica → Delete.
3. Does not impact Writer or other Replicas.

---

## ⚠️ Precautions
- Ensure apps are not using replica.
- Always take a snapshot before deletion if data is critical.

---

## 💡 Real Life Example
- Delete test Aurora cluster after project completion to save costs.
