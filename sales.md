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
