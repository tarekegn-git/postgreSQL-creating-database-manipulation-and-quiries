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

There are several product categories in the merkato market. For example, Cereals, clothes, electronics, etc. Knowing those categories and their pricing is helpful for merchants
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
## 📌 Inserting Values Into the Above Tables

### Insert data into customers table following the table schema created above

```sql

INSERT INTO customers (customer_name, address, city, region, country)
VALUES
  ('Abdulahi Rashid', 'Chelenko', 'Harar', 'Harari', 'Ethiopia'),
  ('Hirut Wondimu', 'Kebele 05', 'Gambela', 'Gambela', 'Ethiopia'),
  ('Mohammed Yusuf', 'Haji Jibril', 'Jijiga', 'Somali', 'Ethiopia'),
  ('Selamawit Girma', 'Lume', 'Mojo', 'Oromia', 'Ethiopia'),
  ('Dereje Tesfaye', 'Jugal', 'Harar', 'Harari', 'Ethiopia'),
  ('Eyob Wubeshet', 'Walal', 'Dembi Dolo', 'Oromia', 'Ethiopia'),
  ('Fatima Abdulkerim', 'Shirkole', 'Gambela', 'Gambela', 'Ethiopia'),
  ('Almaz Tesfaye', 'Sikela', 'Arba Minch', 'South Ethiopia', 'Ethiopia'),
  ('Hassen Teshome', 'Kebele 10', 'Hosaena', 'Central Ethiopia', 'Ethiopia'),
  ('Samuel Gebremedhin', 'Shewa Ber', 'Semera', 'Afar', 'Ethiopia'),
  ('Tsegaye Belay', 'Kebele 02', 'Adigrat', 'Tigray', 'Ethiopia'),
  ('Ahmed Nure', 'Hassen Enclave', 'Moyale', 'Oromia', 'Ethiopia'),
  ('Nasir Ibrahim', 'Becho Bore', 'Worabe', 'Central Ethiopia', 'Ethiopia'),
  ('Omar Farah', 'Geeska', 'Degehabur', 'Somali', 'Ethiopia'),
  ('Fatuma Ahmed', 'Gode 03', 'Gode', 'Somali', 'Ethiopia'),
  ('Tewodros Mekonnen', 'Gojjam Ber', 'Debre Birhan', 'Amhara', 'Ethiopia'),
  ('Rahma Hassan', 'Menaheria', 'Butajira', 'Central Ethiopia', 'Ethiopia'),
  ('Getachew Asfaw', 'Bole', 'Addis Ababa', 'Addis Ababa', 'Ethiopia'),
  ('Fekadu Birhanu', 'Ayder', 'Mekelle', 'Tigray', 'Ethiopia'),
  ('Tamrat Tefera', 'Goba 01', 'Goba', 'Oromia', 'Ethiopia'),
  ('Haimanot Girmay', 'Gebre Guracha', 'Debre Tabor', 'Amhara', 'Ethiopia'),
  ('Muluwork Tadesse', 'Dambel', 'Adama', 'Oromia', 'Ethiopia'),
  ('Wondesen Feleke', 'Kuriftu', 'Bishoftu', 'Oromia', 'Ethiopia'),
  ('Idris Abdulahi', 'Kebele 04', 'Dire Dawa', 'Dire Dawa', 'Ethiopia'),
  ('Saron Abera', 'Gore', 'Metu', 'Oromia', 'Ethiopia'),
  ('Amina Abdurahman', 'Ashewa Meda', 'Harar', 'Harari', 'Ethiopia'),
  ('Girma Hailu', 'Kebele 06', 'Shashemene', 'Oromia', 'Ethiopia'),
  ('Haileyesus Bekele', 'Genet', 'Debre Markos', 'Amhara', 'Ethiopia'),
  ('Helen Berhanu', 'Kidane Mihret', 'Aksum', 'Tigray', 'Ethiopia'),
  ('Bereket Wondwosen', 'Bacho', 'Mizan Teferi', 'Southwest Ethiopia', 'Ethiopia'),
  ('Mekdes Teshome', 'Geremu', 'Wolkite', 'Central Ethiopia', 'Ethiopia'),
  ('Mustafa Ali', 'Jigjiga 02', 'Jijiga', 'Somali', 'Ethiopia'),
  ('Tesfaye Alemu', 'Sabian', 'Dire Dawa', 'Dire Dawa', 'Ethiopia'),
  ('Rediet Solomon', 'Sodo Zuria', 'Wolaita Sodo', 'South Ethiopia', 'Ethiopia'),
  ('Genet Hagos', 'Chilalo', 'Ginir', 'Oromia', 'Ethiopia'),
  ('Yonas Mengistu', 'Kebele 03', 'Asosa', 'Benishangul-Gumuz', 'Ethiopia'),
  ('Birtukan Melese', 'Hetto', 'Hosaena', 'Central Ethiopia', 'Ethiopia'),
  ('Hawa Adem', 'Shewa Robit', 'Debre Berhan', 'Amhara', 'Ethiopia'),
  ('Yunus Ismail', 'Gorgora', 'Gondar', 'Amhara', 'Ethiopia'),
  ('Kalkidan Fekadu', 'Piassa', 'Dessie', 'Amhara', 'Ethiopia'),
  ('Fasil Abate', 'Haro', 'Bule Hora', 'Oromia', 'Ethiopia'),
  ('Lidetu Asrat', 'Arada', 'Gondar', 'Amhara', 'Ethiopia'),
  ('Seble Mulugeta', 'Mendera Kochi', 'Jimma', 'Oromia', 'Ethiopia'),
  ('Mikiyas Demissie', 'Batu 04', 'Batu', 'Oromia', 'Ethiopia'),
  ('Halima Mahamed', 'Berhane Ber', 'Shashamane', 'Oromia', 'Ethiopia'),
  ('Zerihun Taye', 'Tena', 'Dilla', 'South Ethiopia', 'Ethiopia'),
  ('Aster Tekle', 'Kebele 14', 'Bahir Dar', 'Amhara', 'Ethiopia'),
  ('Hussein Ali', 'Sheikh Alimirah', 'Semera', 'Afar', 'Ethiopia'),
  ('Layla Mohammed', 'Sabian', 'Dire Dawa', 'Dire Dawa', 'Ethiopia'),
  ('Meseret Haile', 'Burka', 'Nekemte', 'Oromia', 'Ethiopia'),
  ('Zahra Abubakar', 'Kebele 06', 'Wolkite', 'Central Ethiopia', 'Ethiopia'),
  ('Yared Kassahun', 'Bulale', 'Jijiga', 'Somali', 'Ethiopia'),
  ('Nigist Wolde', 'Kebele 08', 'Gidole', 'South Ethiopia', 'Ethiopia'),
  ('Zewditu Hailemariam', 'Fincha', 'Ambo', 'Oromia', 'Ethiopia'),
  ('Mulugeta Demissie', 'Hawassa Zuria', 'Hawassa', 'Sidama', 'Ethiopia'),
  ('Abdi Mohammed', 'Kaffa 01', 'Bonga', 'Southwest Ethiopia', 'Ethiopia'),
  ('Tigist Alemu', 'Yirgalem 02', 'Yirgalem', 'Sidama', 'Ethiopia');
```
Let's check the data inside customers table

```sql
SELECT * FROM customers LIMIT 5;
 customer_id |  customer_name  |   address   |  city   | region  | country
-------------+-----------------+-------------+---------+---------+----------
           1 | Abdulahi Rashid | Chelenko    | Harar   | Harari  | Ethiopia
           2 | Hirut Wondimu   | Kebele 05   | Gambela | Gambela | Ethiopia
           3 | Mohammed Yusuf  | Haji Jibril | Jijiga  | Somali  | Ethiopia
           4 | Selamawit Girma | Lume        | Mojo    | Oromia  | Ethiopia
           5 | Dereje Tesfaye  | Jugal       | Harar   | Harari  | Ethiopia
(5 rows)

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
