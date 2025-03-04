# PostgreSQL Portfolio

## 🚀 About This Portfolio
Welcome to my PostgreSQL project portfolio! Here, you'll find my database projects, queries, and optimizations.

## 📌 Projects

### 1️⃣ **E-commerce Database Design**
- **Description**: Designed a normalized PostgreSQL database for an e-commerce store.
- **Technologies**: PostgreSQL, pgAdmin, ERD
- **Key Features**:
  - Normalized relational structure
  - Efficient indexing for queries
  - Stored procedures for order management

### 2️⃣ **Performance Optimization in PostgreSQL**
- **Description**: Optimized slow queries in a PostgreSQL database.
- **Techniques Used**:
  - **EXPLAIN ANALYZE**
  - **Indexing Strategies**
  - **Query Optimization**

## 🛠️ Tools & Technologies
- **PostgreSQL 16**
- **pgAdmin**
- **psql (CLI)**
- **DBeaver**
- **SQLAlchemy**

## 📊 Sample Queries
```sql
SELECT customer_name, COUNT(*) AS orders
FROM orders
GROUP BY customer_name
ORDER BY COUNT(*) DESC
LIMIT 10;
