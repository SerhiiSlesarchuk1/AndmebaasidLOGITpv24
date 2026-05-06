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

## XAMPP
lisa
<img width="962" height="598" alt="{92EA4892-D3A0-4CF2-B5AC-22DDD2B39977}" src="https://github.com/user-attachments/assets/a2eaf588-955b-485a-8b9d-65ddd9ebab0c" />
```sql
BEGIN
    INSERT INTO categories(category_name)
    VALUES (uusKategooria);
    SELECT * FROM categories;
END;
```

kustuta
<img width="983" height="595" alt="{291FAEA3-565A-498D-8D3A-C2D0D7DCAF43}" src="https://github.com/user-attachments/assets/162e6865-3b1d-475c-83cd-8ac44a7dc917" />
```sql
BEGIN
    SELECT * FROM categories;
	DELETE FROM categories WHERE category_id=kustutaId;
	SELECT * FROM categories;
END;
```

Suuremhind
<img width="746" height="507" alt="{98F9A04E-0437-474C-B69E-DF24B6E810A9}" src="https://github.com/user-attachments/assets/5e90ef5d-7585-4132-b3f8-61508d8bcd59" />
```sql
BEGIN
    SELECT * FROM products
	WHERE list_ürice > hind;
END;
```

minmaxHind
<img width="833" height="629" alt="{6333796A-9185-492E-BE60-BE89A04BA16E}" src="https://github.com/user-attachments/assets/e14cf918-bf93-4e1f-8afb-f07a3f52999a" />
```sql
BEGIN
    SELECT 
        MIN(list_ürice),
        MAX(list_ürice)
    INTO
        minHind,
        maxHind
    FROM products;
END;
```

muudatus
<img width="798" height="779" alt="{BDEC852A-0B5A-4A48-83F8-037E99E29704}" src="https://github.com/user-attachments/assets/75e4a502-cce8-4a23-85b0-5e581eeb8b59" />
```sql
BEGIN
    SET @sql = CASE 
    WHEN valik LIKE 'add' THEN 
         CONCAT('ALTER TABLE ', tabelinimi, ' ADD ', veerunimi, ' ', tyyp)
    WHEN valik LIKE 'drop' THEN 
         CONCAT('ALTER TABLE ', tabelinimi, ' DROP COLUMN ', veerunimi)
    END;
    PREPARE stmt FROM @sql;
    EXECUTE stmt;
    DEALLOCATE PREPARE stmt;
END;
```
Kõik Tabeli
<img width="699" height="369" alt="{BEAADE5D-F0E1-4BD3-AB4E-62DD1F365F1A}" src="https://github.com/user-attachments/assets/dab851a4-2efe-4f11-8e2a-2449327fb3ce" />

