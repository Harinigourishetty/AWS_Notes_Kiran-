## 📘 1. What is Cache?


Cache is a temporary high-speed storage layer that stores frequently accessed data, so future requests can be served faster.

Instead of repeatedly fetching data from a slow source (like a database), the system first checks the cache.

👉 Think of it as:

#### DB = warehouse (slow but complete)

#### Cache = nearby shelf (fast but limited)

## ⚡ 2. How Cache Reduces Load on Database

### Without Cache:

Every request goes to the database.

User → App → Database → App → User

Problems:

High latency

Database overload

Poor scalability

### With Cache:

Data is served from cache when possible.

User → App → Cache → (if miss → DB)

### Flow:

App checks cache

If cache hit → return instantly

If cache miss:

Fetch from DB

Store in cache

Return response

### 🔥 Benefits:

Reduces DB queries

Faster response time

Handles more traffic

Lower infrastructure cost

## 🧠 3. Types of Cache (Where Cache Operates)

Cache exists at multiple layers:

### 🖥️ 1. Client-side Cache

-> Browser cache

-> Stores static files (CSS, JS, images)

### 🌐 2. CDN Cache

-> Example: Cloudflare, Akamai

-> Stores content closer to users globally

### ⚙️ 3. Application-Level Cache

-> In-memory caching

-> Tools:

-> Redis

-> Memcached

#### Used for:

-> API responses

-> Query results

-> Sessions

### 🗄️ 4. Database Cache

-> Built-in DB caching (query cache, buffer cache)

-> Reduces disk reads

### 🧩 5. OS / Hardware Cache

-> CPU cache (L1/L2/L3)

-> RAM buffering

## 🔁 4. Cache Strategies

### 1. Cache-Aside (Lazy Loading) ✅ Most common

App loads data into cache when needed

### 2. Write-Through

Write to cache + DB simultaneously

### 3. Write-Back (Write-Behind)

Write to cache first, DB later (async)

### 4. Read-Through

Cache fetches data automatically

## ⚖️ 5. Before Cache vs After Cache

### ❌ Before Cache

#### Aspect/ Behavior

Requests/ All hit DB

Latency/ High

DB Load/	Heavy

Scalability/	Poor

Cost/	High

### ✅ After Cache

#### Aspect/	Behavior

Requests/	Mostly served from cache

Latency/	Low

DB Load/	Reduced

Scalability/	High

Cost/	Lower

### 📊 Example

#### Without cache:

1000 requests → 1000 DB queries

#### With cache:

1000 requests → ~100 DB queries (assuming 90% hit rate)

## 🧱 6. Where Cache Fits in Architecture

User ↓ CDN (optional) ↓ Load Balancer ↓ Application Server ↓ Cache (Redis) ↓ Database

## 🧩 7. What is PgBouncer?

PgBouncer is a lightweight connection pooler for PostgreSQL.

❗ Problem It Solves

Databases like PostgreSQL are bad at handling too many connections.

Each connection:

Uses memory

Consumes CPU

Slows down DB when too many exist

### 💡 Solution: PgBouncer

Acts as a middle layer between app and database.

App → PgBouncer → PostgreSQL

### 🔄 How It Works

Maintains a pool of reusable DB connections

Apps connect to PgBouncer instead of DB

PgBouncer reuses connections efficiently

### ⚙️ Pooling Modes

#### 1. Session Pooling

One client = one DB connection (until session ends)

#### 2. Transaction Pooling ⭐ Most popular

Connection assigned per transaction

Released immediately after

#### 3. Statement Pooling

Per query (rarely used)

🚀 Benefits of PgBouncer

Reduces connection overhead

Improves DB performance

Prevents connection exhaustion

Handles high concurrency

### 🔁 PgBouncer vs Cache

Feature	Cache	PgBouncer

Purpose	Store data	Manage connections

Reduces DB load	✅ Yes	❌ No (indirect only)

Speeds queries	✅ Yes	❌ No

Handles traffic	✅ Yes	✅ Yes

Data storage	Yes	No

### 👉 Important:

Cache reduces number of queries

PgBouncer optimizes how queries reach DB

## 🧠 8. Cache + PgBouncer Together

Best practice:

User ↓ App ↓ Cache (Redis) ↓ PgBouncer ↓ PostgreSQL

### Flow:

Cache hit → DB not touched

Cache miss → PgBouncer efficiently connects to DB

## 🧾 9. Key Takeaways
Cache = speed + fewer DB queries

PgBouncer = efficient DB connection handling

Use both together for scalable systems

Most performance gains come from good caching strategy