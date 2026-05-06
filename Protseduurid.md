## SQL protseduur -
store protseduur - salvestatud protseduurid - sama mis on funktsioonid programmerimises, mingi tagevus, mis on salvestatud andmebaasi, ja mida saab automaatselt teha (INSERT, UPDATE, SELECT, UPDATE)

```sql
Create database protseduuriSlesarchuk;
use protseduuriSlesarchuk

--1 categories
create table categories(
category_id int PRIMARY KEY identity(1,1),
category_name varchar(25) UNIQUE);

SELECT * FROM categories

CREATE Procedure lisaKategooria

@ussKategooria varchar(30)
AS
BEGIN
--Kirjatus
INSERT INTO categories(category_name)
VALUES (@ussKategooria);
SELECT * FROM categories;
END;
```
<img width="274" height="277" alt="{BB1BC15A-BD76-447F-BCE9-1A4CD6A74969}" src="https://github.com/user-attachments/assets/d5bae16c-2f8f-4e6d-9535-70ccc4fe67f2" />
<img width="289" height="134" alt="{7120EFA3-048E-4E8A-88D9-0C549FFFC6B2}" src="https://github.com/user-attachments/assets/4af34952-b111-4bab-9c00-7c44ae5e34d9" />
