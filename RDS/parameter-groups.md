# 🔹 Amazon RDS – Parameter Groups

## 📖 Definition
- Parameter Groups are **config sets** controlling DB engine behavior.
- Two types:
  - **DB Parameter Group** → Instance-level parameters.
  - **DB Cluster Parameter Group** → Cluster-wide parameters.

---

## ⚙️ Examples of Parameters
- `max_connections` → Maximum DB connections.
- `autocommit` → Auto commit behavior.
- `work_mem` → Memory for query operations.

---

## 🛠️ Steps – Change RDS Configurations
1. Go to **RDS Console → Parameter Groups**.
2. Create new group → Select DB engine & version.
3. Modify parameters (example: increase `max_connections`).
4. Apply parameter group to DB.
5. Reboot DB if needed.

---

## 🌍 Real Life Example
- Trading app: Increase `max_connections` to handle more concurrent users.
- Analytics app: Increase `work_mem` for faster query performance.
