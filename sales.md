## andmebaadsales
```sql
--1.categories
CREATE TABLE categories(
category_id int PRIMARY KEY identity(1,1),
category_name varchar(25) UNIQUE);

INSERT INTO categories(category_name)
VALUES ('Ruuter');

SELECT * FROM categories;
```
<img width="193" height="77" alt="{6E10D770-0D91-4B8F-8A02-56B1E6C2B6C0}" src="https://github.com/user-attachments/assets/1c78b1b7-0bba-434a-8764-2f1daf10bd80" />

```sql
--2.brands
CREATE TABLE brands(
brand_id int PRIMARY KEY identity(1,1),
brand_name varchar(15) UNIQUE);

INSERT INTO brands(brand_name)
VALUES ('Samsung');

SELECT * FROM brands;
```
<img width="167" height="79" alt="{B469ACD5-0C79-4CCE-AC78-B8CE0DC1CD83}" src="https://github.com/user-attachments/assets/ae739f51-c1e9-4534-8565-5db8576119c1" />

```sql
--3.products
Create TABLE products(
product_id int PRIMARY KEY identity(1,1),
product_name varchar(50) not null,
brand_id int,
FOREIGN KEY (brand_id) references brands(brand_id),
category_id int,
FOREIGN KEY (category_id) references categories(category_id),
model_year int,
list_ürice money);

INSERT INTO products
VALUES ('nutitelefon X10',1, 1, 2025, 500);

select * from products;
```
<img width="440" height="80" alt="{8E85FD75-0FBA-4E81-AE2F-02A2C48F7DBC}" src="https://github.com/user-attachments/assets/4e3a8dc5-3d23-4a0b-b1e0-644a0636bc19" />

```sql
--4.stores
CREATE TABLE stores(
store_id int PRIMARY KEY identity(1,1),
store_name varchar(20) not null,
phone varchar(13),
email varchar(20),
street varchar(21),
city varchar(15),
state varchar(10),
zip_code char(5)
)

INSERT INTO stores
VALUES ('Ülemiste', 'iphone', 'ülemiste@gmail.com', 'ülemiste tee', 'Tallinn', 'Eesti', '10319');

SELECT * FROM stores;
```
