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
### 1) Create Customers table

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
### 2) Create Products table
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
### 3) Create a Product categories table

There are several product categories in the merkato market. For example, Cereals, clothes, electronics, etc. Knowing those categories and their pricing is helpful for merchants
Therefore, here we can create another table named product_categories
 
  ```sql
CREATE TABLE product_categories ( 
  category_id SERIAL NOT NULL PRIMARY KEY,
  category_name VARCHAR(255),
  description VARCHAR(255)
); 
```
### 4) Create Orders table
Orders table contain selling or buying information among merchants(customers)

```sql
DROP TABLE orders;
CREATE TABLE orders ( 
  order_id SERIAL NOT NULL PRIMARY KEY,
  customer_id INT,
  order_date DATE
);

```
## 📌 Inserting Values into the Above Tables

### 1) Insert data into customers table following the table schema created above

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
Let's check the data inside the customer's table

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
### 2) Insert Data into Products table

```sql
INSERT INTO products (product_name, category_id, unit, price)  
VALUES
  -- Grains & Pulses (category_id = 1)
  ('Teff', 1, 'kg', 52.00),
  ('Wheat', 1, 'kg', 35.50),
  ('Barley', 1, 'kg', 28.75),
  ('Maize', 1, 'kg', 24.00),
  ('Sorghum', 1, 'kg', 26.50),
  ('Lentils', 1, 'kg', 50.00),
  ('Chickpeas', 1, 'kg', 47.00),
  ('Peas', 1, 'kg', 38.00),

  -- Spices & Condiments (category_id = 2)
  ('Berbere', 2, 'kg', 150.00),
  ('Mitmita', 2, 'kg', 140.00),
  ('Shiro Powder', 2, 'kg', 90.00),
  ('Turmeric', 2, 'kg', 120.00),
  ('Ginger', 2, 'kg', 80.00),
  ('Black Cumin', 2, 'kg', 95.00),
  ('Fenugreek', 2, 'kg', 65.00),
  ('Basil', 2, 'bunch', 15.00),

  -- Vegetables & Fruits (category_id = 3)
  ('Tomato', 3, 'kg', 30.00),
  ('Onion', 3, 'kg', 22.00),
  ('Garlic', 3, 'kg', 140.00),
  ('Cabbage', 3, 'kg', 18.00),
  ('Carrot', 3, 'kg', 25.00),
  ('Potato', 3, 'kg', 20.00),
  ('Banana', 3, 'kg', 35.00),
  ('Avocado', 3, 'kg', 50.00),
  ('Papaya', 3, 'kg', 45.00),
  ('Mango', 3, 'kg', 40.00),
  ('Lemon', 3, 'kg', 30.00),
  ('Orange', 3, 'kg', 38.00),

  -- Meat & Dairy (category_id = 4)
  ('Beef', 4, 'kg', 350.00),
  ('Goat Meat', 4, 'kg', 300.00),
  ('Sheep Meat', 4, 'kg', 320.00),
  ('Chicken', 4, 'kg', 280.00),
  ('Milk', 4, 'liter', 35.00),
  ('Cheese', 4, 'kg', 150.00),
  ('Butter', 4, 'kg', 400.00),
  ('Eggs', 4, 'dozen', 100.00),

  -- Coffee & Beverages (category_id = 5)
  ('Ethiopian Coffee Beans', 5, 'kg', 400.00),
  ('Tea Leaves', 5, 'kg', 200.00),
  ('Sugar', 5, 'kg', 60.00),
  ('Honey', 5, 'kg', 250.00),

  -- Oils & Cooking Essentials (category_id = 6)
  ('Sunflower Oil', 6, 'liter', 120.00),
  ('Palm Oil', 6, 'liter', 110.00),
  ('Sesame Oil', 6, 'liter', 180.00),
  ('Groundnut Oil', 6, 'liter', 170.00),

  -- Textiles & Clothing (category_id = 7)
  ('Gabi (Traditional Blanket)', 7, 'piece', 450.00),
  ('Netela (Traditional Scarf)', 7, 'piece', 200.00),
  ('T-shirts', 7, 'piece', 300.00),
  ('Jeans', 7, 'pair', 800.00),
  ('Shoes', 7, 'pair', 1200.00),
  ('Handwoven Shawl', 7, 'piece', 350.00),

  -- Electronics (category_id = 8)
  ('Mobile Phone', 8, 'piece', 7500.00),
  ('Laptop', 8, 'piece', 45000.00),
  ('Charger', 8, 'piece', 500.00),
  ('Earphones', 8, 'piece', 1500.00),
  ('Solar Panel', 8, 'piece', 8000.00),

  -- Household Items (category_id = 9)
  ('Injera Stove', 9, 'piece', 1800.00),
  ('Clay Jebena (Coffee Pot)', 9, 'piece', 300.00),
  ('Plastic Chair', 9, 'piece', 450.00),
  ('Charcoal Stove', 9, 'piece', 600.00),
  ('Washing Powder', 9, 'kg', 250.00),

  -- Construction Materials (category_id = 10)
  ('Cement', 10, 'bag', 650.00),
  ('Sand', 10, 'm³', 800.00),
  ('Rebar', 10, 'piece', 250.00),
  ('Corrugated Iron Sheets', 10, 'piece', 1200.00),
  ('Timber', 10, 'm³', 5000.00),
  ('Paint', 10, 'liter', 450.00),

  -- Miscellaneous (category_id = 11)
  ('Pen', 11, 'piece', 15.00),
  ('Toothpaste', 11, 'tube', 80.00),
  ('Soap', 11, 'bar', 50.00),
  ('Tire', 11, 'piece', 3000.00),
  ('Motor Oil', 11, 'liter', 850.00),
  ('Battery', 11, 'piece', 200.00),
  ('Flashlight', 11, 'piece', 500.00),
  ('Bicycle', 11, 'piece', 15000.00),
  ('Motorcycle', 11, 'piece', 75000.00),
  ('Wheelbarrow', 11, 'piece', 3500.00);

```
Let's see if product records are correctly inserted

```sql
SELECT * FROM products LIMIT 5;
 product_id | product_name | category_id | unit | price
------------+--------------+-------------+------+-------
         77 | Teff         |           1 | kg   | 52.00
         78 | Wheat        |           1 | kg   | 35.50
         79 | Barley       |           1 | kg   | 28.75
         80 | Maize        |           1 | kg   | 24.00
         81 | Sorghum      |           1 | kg   | 26.50
(5 rows)


merkato_market=#

```
### Insert Data into Product Categories table

```sql
INSERT INTO product_categories (category_name, description) 
VALUES
  ('Grains & Pulses', 'Includes teff, wheat, barley, maize, sorghum, lentils, chickpeas, and peas'),
  ('Spices & Condiments', 'Includes berbere, mitmita, shiro powder, turmeric, ginger, and black cumin'),
  ('Vegetables & Fruits', 'Includes tomatoes, onions, garlic, cabbage, carrots, potatoes, bananas, and avocados'),
  ('Meat & Dairy', 'Includes beef, goat meat, sheep meat, chicken, milk, cheese, butter, and eggs'),
  ('Coffee & Beverages', 'Includes Ethiopian coffee beans, tea leaves, sugar, and honey'),
  ('Oils & Cooking Essentials', 'Includes sunflower oil, palm oil, sesame oil, and groundnut oil'),
  ('Textiles & Clothing', 'Includes gabi, netela, t-shirts, jeans, shoes, and handwoven shawls'),
  ('Electronics', 'Includes mobile phones, laptops, chargers, earphones, and solar panels'),
  ('Household Items', 'Includes injera stoves, clay jebena, plastic chairs, charcoal stoves, and washing powder'),
  ('Construction Materials', 'Includes cement, sand, rebar, corrugated iron sheets, timber, and paint'),
  ('Miscellaneous', 'Includes notebooks, pens, toothpaste, soap, tires, motor oil, batteries, flashlights, bicycles, and motorcycles');
```
```sql

SELECT * FROM product_categories LIMIT 5;
 category_id |    category_name    |                                     description
-------------+---------------------+--------------------------------------------------------------------------------------
           1 | Grains & Pulses     | Includes teff, wheat, barley, maize, sorghum, lentils, chickpeas, and peas
           2 | Spices & Condiments | Includes berbere, mitmita, shiro powder, turmeric, ginger, and black cumin
           3 | Vegetables & Fruits | Includes tomatoes, onions, garlic, cabbage, carrots, potatoes, bananas, and avocados
           4 | Meat & Dairy        | Includes beef, goat meat, sheep meat, chicken, milk, cheese, butter, and eggs
           5 | Coffee & Beverages  | Includes Ethiopian coffee beans, tea leaves, sugar, and honey
(5 rows)


merkato_market=#
```
### Insert Data into the Orders table.
Note: The Data is according to Ethiopian calendar
```sql
INSERT INTO orders (customer_id, order_date) 
VALUES
  (10, '2017-09-01'),
  (15, '2017-09-02'),
  (20, '2017-09-03'),
  (25, '2017-09-04'),
  (30, '2017-09-05'),
  (35, '2017-09-06'),
  (40, '2017-09-07'),
  (45, '2017-09-08'),
  (50, '2017-09-09'),
  (55, '2017-09-10'),
  (60, '2017-09-11'),
  (65, '2017-09-12'),
  (70, '2017-09-13'),
  (75, '2017-09-14'),
  (80, '2017-09-15'),
  (85, '2017-09-16'),
  (90, '2017-09-17'),
  (95, '2017-09-18'),
  (10, '2017-09-19'),
  (15, '2017-09-20'),
  (20, '2017-09-21'),
  (25, '2017-09-22'),
  (30, '2017-09-23'),
  (35, '2017-09-24'),
  (40, '2017-09-25'),
  (45, '2017-09-26'),
  (50, '2017-09-27'),
  (55, '2017-09-28'),
  (60, '2017-09-29'),
  (65, '2017-09-30'),
  (70, '2017-10-01'),
  (75, '2017-10-02'),
  (80, '2017-10-03'),
  (85, '2017-10-04'),
  (90, '2017-10-05'),
  (95, '2017-10-06'),
  (10, '2017-10-07'),
  (15, '2017-10-08'),
  (20, '2017-10-09'),
  (25, '2017-10-10'),
  (30, '2017-10-11'),
  (35, '2017-10-12'),
  (40, '2017-10-13'),
  (45, '2017-10-14'),
  (50, '2017-10-15'),
  (55, '2017-10-16'),
  (60, '2017-10-17'),
  (65, '2017-10-18'),
  (70, '2017-10-19'),
  (75, '2017-10-20'),
  (80, '2017-10-21'),
  (85, '2017-10-22'),
  (90, '2017-10-23'),
  (95, '2017-10-24'),
  (10, '2017-10-25'),
  (15, '2017-10-26'),
  (20, '2017-10-27'),
  (25, '2017-10-28'),
  (30, '2017-10-29'),
  (35, '2017-10-30'),
  (40, '2017-11-01'),
  (45, '2017-11-02'),
  (50, '2017-11-03'),
  (55, '2017-11-04'),
  (60, '2017-11-05'),
  (65, '2017-11-06'),
  (70, '2017-11-07'),
  (75, '2017-11-08'),
  (80, '2017-11-09'),
  (85, '2017-11-10'),
  (90, '2017-11-11'),
  (95, '2017-11-12'),
  (10, '2017-11-13'),
  (15, '2017-11-14'),
  (20, '2017-11-15'),
  (25, '2017-11-16'),
  (30, '2017-11-17'),
  (35, '2017-11-18'),
  (40, '2017-11-19'),
  (45, '2017-11-20'),
  (50, '2017-11-21'),
  (55, '2017-11-22'),
  (60, '2017-11-23');
```
Let's see what information inside orders table
```sql
SELECT * FROM orders LIMIT 5;
 order_id | customer_id | order_date
----------+-------------+------------
        1 |          10 | 2017-09-01
        2 |          15 | 2017-09-02
        3 |          20 | 2017-09-03
        4 |          25 | 2017-09-04
        5 |          30 | 2017-09-05
(5 rows)


merkato_market=#
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
