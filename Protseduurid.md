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
<img width="317" height="134" alt="{90AEFBFB-4A4A-4CF3-B608-6827223E4CA9}" src="https://github.com/user-attachments/assets/c1a0c459-9077-4127-9b27-d9e7a651c8ac" />

## Protseduur veeru lisamiseks või kustutamiseks 
<img width="513" height="327" alt="{11897C46-7C8D-45F8-87B2-BF949DA0C62A}" src="https://github.com/user-attachments/assets/c2fc5d56-b230-4c90-81c0-12b05f1ff539" />

kustutamiseks 
<img width="518" height="273" alt="{A32A71D8-6634-49F5-A1EA-A5D8F1DB8F38}" src="https://github.com/user-attachments/assets/73590784-1361-4855-a989-9ef397446d12" />
