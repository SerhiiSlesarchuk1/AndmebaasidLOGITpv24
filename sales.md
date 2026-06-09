[<img src="https://img.shields.io/badge/🏠_Pealeht-README-gray?style=flat" />](README.md) [<img src="https://img.shields.io/badge/🔸_Juhend-CREATE_INSERT-orange?style=flat" />](CREATE_IMSERT.md) [<img src="https://img.shields.io/badge/🟩_Kasutajad-Kasutaja.md-green?style=flat" />](Kasutaja.md) [<img src="https://img.shields.io/badge/🟪_Veebipood-sales.md-teal?style=flat" />](sales.md) [<img src="https://img.shields.io/badge/🟥_Päästikud_(MySQL)-Triger.md-red?style=flat" />](Triger.md) [<img src="https://img.shields.io/badge/🟥_Päästikud_(XAMPP)-TrigerXAMMP.md-red?style=flat" />](TrigerXAMMP.md) [<img src="https://img.shields.io/badge/🟪_Protseduurid-Protseduurid.md-purple?style=flat" />](Protseduurid.md) [<img src="https://img.shields.io/badge/🟥_Keys (MySQL)-Keys.md-red?style=flat" />](Keys.md)
--
# VEEBIPOOD
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
<img width="303" height="92" alt="{692785D5-7329-4724-8195-938659510AE1}" src="https://github.com/user-attachments/assets/a0741226-b8e8-46bf-91f4-47589a93cb35" />

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
<img width="288" height="90" alt="{4C110DFC-EADF-4576-ACED-49AA1009F5C3}" src="https://github.com/user-attachments/assets/bdeeee07-b71e-4531-9a49-2c41daa7b904" />

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
<img width="299" height="108" alt="{61CA9994-74E1-4104-B7D1-AF64448BF842}" src="https://github.com/user-attachments/assets/70ed0e59-1c7c-4181-a057-167c116ddb6c" />

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
<img width="601" height="80" alt="{0EED95FA-F3FB-4E41-B12A-225E6885D7C8}" src="https://github.com/user-attachments/assets/3c754e40-0576-4d0a-ba2c-27771f4f4c82" />
<img width="290" height="73" alt="{53A2B0F5-B85B-4D25-A339-D6CE4045FCBA}" src="https://github.com/user-attachments/assets/751a6598-dcb4-4993-bc5b-d0d18af599e0" />


```sql
--5.stocks
CREATE TABLE stocks(
store_id int,
product_id int,
PRIMARY KEY (store_id, product_id),
FOREIGN KEY (store_id) references stores(store_id),
FOREIGN KEY (product_id) references products(product_id),

quantity int 
)

INSERT INTO stocks
VALUES (1, 1, 4)

SELECT * FROM stocks;
```
<img width="221" height="94" alt="{EF631501-4081-4F48-8080-FADB53488B4D}" src="https://github.com/user-attachments/assets/c8674e9a-1d92-42fb-8670-503b4abe91d3" />
<img width="286" height="107" alt="{C59FB02A-7B9B-4010-BD8D-1491F453082A}" src="https://github.com/user-attachments/assets/5f35df84-48c3-4104-952f-b591da0984a6" />


```sql
--6.customers
create table customers(
customer_id int primary key identity(1,1),
first_name varchar(15) not null,
last_name varchar(15) not null,
phone varchar(13),
email varchar(20),
street varchar(15),
city varchar(15) check (city='Tallinn' or city='Narva'),
zip_code char(5)
)

insert into customers
values('Andrei', 'Lomov', '52637294', 'andrei@gmail.com', 'Ülemiste tee', 'Tallinn','13912');

select * from customers
```
<img width="661" height="95" alt="{499A69AA-4566-49E4-BC78-650B5C15213E}" src="https://github.com/user-attachments/assets/5d299752-ebd9-4b0f-b351-80f195a7af7b" />
<img width="309" height="72" alt="{E7963FF5-1660-44E2-A49A-FF03EF88828E}" src="https://github.com/user-attachments/assets/12958fb1-3d30-4b62-a3fe-1374be2d3218" />

```sql
--7.staff
create table staff(
staff_id int primary key identity(1,1),
first_name varchar(15) not null,
last_name varchar(15) not null,
email varchar(20),
phone varchar(13),
active bit,
store_id int,
foreign key (store_id) references stores(store_id),
manager bit
);

insert into staff
values('Irina', 'Rahva', 'irina@gmail.com', '52635494', 1, 1, 1);

select * from staff;
```
<img width="546" height="80" alt="{0ACAB392-F42B-4EAE-AB8C-986F228F0546}" src="https://github.com/user-attachments/assets/82686a96-b26c-4300-b4ec-0334e247414e" />
<img width="258" height="94" alt="{6520087C-89D0-4845-9D70-ADF0AF36EF1D}" src="https://github.com/user-attachments/assets/fb16ccc6-9f4b-492c-ad50-5649d98fc1f2" />

```sql
--8. orders
create table orders(
order_id int PRIMARY KEY identity (1,1),
customer_id int,
order_status varchar(15) check(order_status='complete' or order_status='incomplete'),
order_date  Date,
required_date Date,
shipped_date Date,
store_id int,
staff_id int,
foreign key (customer_id) references customers(customer_id),
foreign key (store_id) references stores(store_id),
foreign key (staff_id) references staff(staff_id)
);

insert into orders
values (1, 'incomplete', '2026-04-25', '2026-06-1', '2026-05-29', 1, 3);

select * from orders;
```
<img width="603" height="85" alt="{C04BADF8-E661-4A06-92E1-F86B538490C4}" src="https://github.com/user-attachments/assets/dc4ecde2-7b2a-47ec-b4fa-71201385eb33" />
<img width="285" height="129" alt="{938367AA-9D5A-44F8-BE8B-EBE36C597F5F}" src="https://github.com/user-attachments/assets/396561fd-4c85-400f-9ccc-75d1b78d2e8c" />

```sql
--9.order_items
create table order_items(
order_id int,
item_id int,
primary key (order_id, item_id),
product_id int,
quantity int,
list_price money,
discount int,
foreign key (order_id) references orders(order_id),
foreign key (product_id) references products(product_id)
);

insert into order_items
values (2, 2, 1, 150, 1230, 90);

select * from order_items;
```
<img width="383" height="104" alt="{28A826F5-ABEE-485B-A454-66C42437CE79}" src="https://github.com/user-attachments/assets/d085bbd3-683e-4e6b-bc4c-80ee9b273587" />
<img width="273" height="109" alt="{6B9D6C58-AEB8-4A3C-9056-A9F36A10C3DA}" src="https://github.com/user-attachments/assets/7d609e4f-3185-42ba-9480-435f728fd5c0" />


Database diagramm
<img width="1005" height="725" alt="{52350954-643F-4904-BB5B-3C8B25F5050F}" src="https://github.com/user-attachments/assets/863e892e-aef7-40e3-b887-830ed2bb112f" />



