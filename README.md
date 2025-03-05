# PostgreSQL Database Creation and Queries

## 🚀 About This Project
Welcome to my PostgreSQL project! In this PostgreSQL project, I will create a database named `merkato_market` which contains four tables such as `products, customers, product_categories
and orders`. Merkato market in Addis Ababa has hundreds of various items sold and bought by customers. The products table contains information 
about those items. Each product is categorized under the `product_categories` table, which contains information about product categories. For example, Teff and laptop are evidently under different categories. Finally, the `orders` table contains orders(selling and buying) by merkato customers, which means merchants from all over Ethiopia. After creating the database, I will conduct some queries to demonstrate the application of PostgreSQL for getting insights into the database. 

## 📌 Creating Merkato Market Database 
Open SQL Shell terminal of PostgreSQL and type the following command
```sql

CREATE DATABASE merkato_market

Server [localhost]:
Database [postgres]:
Port [5432]:
Username [postgres]:
Password for user postgres:
psql (16.8)
WARNING: Console code page (437) differs from Windows code page (1252)
         8-bit characters might not work correctly. See the psql reference
         page "Notes for Windows users" for details.
Type "help" for help.
```
After creating the database, we need to connect to it to create the tables
```sql
postgres=# \c merkato_market;
You are now connected to database "merkato_market" as user "postgres".

```
## 📌 Creating customers, products, product_categories and orders table 

Under `merkato_market`, let's create 4 tables
### Create Customers table

First, let's create a customer table that would include Ethiopian merchants who do business(selling and buying) in Merkato, Addis Ababa. The column values are very easy to understand.
The customer_id column automatically increments whenever a new record is added to the database

```sql
CREATE TABLE customers (
  customer_id SERIAL NOT NULL PRIMARY KEY,
  customer_name VARCHAR(255),
  address VARCHAR(255),
  city VARCHAR(255),
  region VARCHAR(255),
  country VARCHAR(255)
);

```
### Create Products table
A database table of information about products in the merkato market

```sql

CREATE TABLE products (
  product_id SERIAL NOT NULL PRIMARY KEY,
  product_name VARCHAR(255),
  category_id INT,
  unit VARCHAR(255),
  price DECIMAL(10, 2)
);

```
### Create a Product categories table

There are several product categories in the merkato market. for example, Cereals, clothes, electroncs etc. knowing those categories and their pricing is helpful for merchats
Therefore, here we can create another table named product_categories
 
  ```sql
CREATE TABLE product_categories ( 
  category_id SERIAL NOT NULL PRIMARY KEY,
  category_name VARCHAR(255),
  description VARCHAR(255)
); 
```
### Create Orders table
Orders table contain selling or buying information among merchants(customers)

```sql
DROP TABLE orders;
CREATE TABLE orders ( 
  order_id SERIAL NOT NULL PRIMARY KEY,
  customer_id INT,
  order_date DATE
);

```

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
