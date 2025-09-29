# 🔹 Amazon Aurora – Endpoints

## 📖 Definition
Endpoints are **connection points** to interact with Aurora DB Cluster.  
They allow apps to direct **reads and writes** properly.

---

## 📌 Types of Endpoints

### 1. Writer Endpoint
- Connects to **Primary Instance (Writer)**.
- Handles all **read + write queries**.
- Only one writer per cluster.

### 2. Reader Endpoint
- Connects to **Replica Instances**.
- Handles **read-only queries**.
- Provides **load balancing** across multiple replicas.

### 3. Instance Endpoint
- Directly connects to a **specific instance** (writer or reader).
- Used for debugging, monitoring, or admin tasks.

### 4. Custom Endpoint
- User-defined group of DB instances.
- Example: Group only replicas used for analytics.

---

## 🌍 Real Life Example
- **E-commerce website**:
  - Writer Endpoint → Order placement.
  - Reader Endpoint → Browsing products.
  - Custom Endpoint → Analytics queries by BI team.
