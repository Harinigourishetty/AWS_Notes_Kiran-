# 1. SQL vs NoSQL

## 🔹 SQL (Structured Query Language)

**Definition:**
 A type of database that stores data in **tables (rows and columns)** with a **fixed schema**.

**Key characteristics:**

- Structured and predefined schema
- Uses SQL language (SELECT, INSERT, etc.)
- Strong consistency (ACID properties)
- Best for relational data

**Examples:**

- MySQL
- PostgreSQL
- Oracle

**Simple example:**
 Table: `Users`

| ID   | Name | Age  |
| ---- | ---- | ---- |
| 1    | Ravi | 25   |
| 2    | Anya | 30   |

Query:

```
SELECT * FROM Users WHERE Age > 25;
```

------

## 🔹 NoSQL (Not Only SQL)

**Definition:**
 A type of database designed for **flexible, unstructured, or semi-structured data**.

**Key characteristics:**

- No fixed schema
- Scales horizontally easily
- Handles large volumes of data
- Types: Document, Key-Value, Graph, Column

**Examples:**

- MongoDB (Document)
- Redis (Key-Value)
- Cassandra (Column)

**Simple example (MongoDB document):**

```
{
  "name": "Ravi",
  "age": 25,
  "hobbies": ["cricket", "music"]
}
```

------

## 🔹 SQL vs NoSQL (Quick Comparison)

| Feature     | SQL             | NoSQL                   |
| ----------- | --------------- | ----------------------- |
| Schema      | Fixed           | Flexible                |
| Data format | Tables          | JSON, key-value, etc.   |
| Scalability | Vertical        | Horizontal              |
| Best for    | Structured data | Big / unstructured data |
| Consistency | Strong (ACID)   | Eventual (often)        |

------

# 2. RTO vs RPO

These are used in **disaster recovery**.

## 🔹 RTO (Recovery Time Objective)

**Definition:**
 The **maximum acceptable time** to restore a system after failure.

**Simple meaning:**
 “How fast should we recover?”

**Example:**

- RTO = 2 hours
   → System must be back within 2 hours after a crash

------

## 🔹 RPO (Recovery Point Objective)

**Definition:**
 The **maximum acceptable data loss** measured in time.

**Simple meaning:**
 “How much data can we afford to lose?”

**Example:**

- RPO = 10 minutes
   → You can lose only last 10 minutes of data

------

## 🔹 RTO vs RPO (Quick Comparison)

| Aspect   | RTO                      | RPO                          |
| -------- | ------------------------ | ---------------------------- |
| Focus    | Time to recover          | Data loss tolerance          |
| Question | “How fast to recover?”   | “How much data can we lose?” |
| Example  | 2 hours downtime allowed | 10 min data loss allowed     |

------

# 3. SLA vs SLO vs SLI

These are used in **service reliability and performance tracking**.

------

## 🔹 SLI (Service Level Indicator)

**Definition:**
 A **metric** that measures performance.

**Simple meaning:**
 “What are we measuring?”

**Examples:**

- Request latency = 200 ms
- Uptime = 99.9%
- Error rate = 1%

------

## 🔹 SLO (Service Level Objective)

**Definition:**
 A **target value** for an SLI.

**Simple meaning:**
 “What is our goal?”

**Examples:**

- 99.9% uptime
- Response time < 300 ms

------

## 🔹 SLA (Service Level Agreement)

**Definition:**
 A **formal contract** between provider and customer that includes penalties if targets are not met.

**Simple meaning:**
 “What happens if we fail?”

**Examples:**

- If uptime drops below 99.9%, customer gets refund
- Support must respond within 1 hour

------

## 🔹 SLA vs SLO vs SLI (Quick Comparison)

| Term | Meaning     | Focus              | Example                  |
| ---- | ----------- | ------------------ | ------------------------ |
| SLI  | Measurement | Metrics            | Response time = 200 ms   |
| SLO  | Target      | Goals              | 95% requests < 300 ms    |
| SLA  | Contract    | Business agreement | Refund if uptime < 99.9% |

------

# 🔚 Simple Analogy (All Three Together)

Think of a food delivery app:

- **SLI:** Delivery time = 25 minutes
- **SLO:** Deliver within 30 minutes
- **SLA:** If late → customer gets ₹100 coupon

------

# ✅ Quick Summary

- **SQL vs NoSQL** → How data is stored
- **RTO vs RPO** → Disaster recovery goals
- **SLA vs SLO vs SLI** → Service performance & commitments