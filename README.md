# PostgreSQL Database Creation and Queries

## 🚀 About This Project
Welcome to my PostgreSQL project! In this PostgreSQL project, I will create a database named `merkato_market` which contains four tables such as `products, customers, product_categories
and orders`. Merkato market in Addis Ababa has hundreds of various items sold and bought by customers. The products table contains information 
about those items. Each product is categorized under the `product_categories` table, which contains information about product categories. For example, Teff and laptop are evidently under different categories. Finally, the `orders` table contains orders(selling and buying) by merkato customers, which means merchants from all over Ethiopia. After creating the database, I will conduct some queries to demonstrate the application of PostgreSQL for getting insights into the database. 

## 📌 Creating Merkato Market Database 

```sql

CREATE DATABASE merkato_market

```

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
