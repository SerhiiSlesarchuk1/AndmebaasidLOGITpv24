## AndmebaasidLOGITpv24
admebaaside haldusega seotud sql kood ja konspektid

## 📂 Projekti sisujuht

[<img src="https://img.shields.io/badge/🏠_Pealeht-README-gray?style=flat" />](README.md) [<img src="https://img.shields.io/badge/🔸_Juhend-CREATE_INSERT-orange?style=flat" />](CREATE_IMSERT.md) [<img src="https://img.shields.io/badge/🟩_Kasutajad-Kasutaja.md-green?style=flat" />](Kasutaja.md) [<img src="https://img.shields.io/badge/🟪_Veebipood-sales.md-teal?style=flat" />](sales.md) [<img src="https://img.shields.io/badge/🟥_Päästikud_(MySQL)-Triger.md-red?style=flat" />](Triger.md) [<img src="https://img.shields.io/badge/🟥_Päästikud_(XAMPP)-TrigerXAMMP.md-red?style=flat" />](TrigerXAMMP.md) [<img src="https://img.shields.io/badge/🟪_Protseduurid-Protseduurid.md-purple?style=flat" />](Protseduurid.md)
---

## Põhimõisted
- Andmebaasi haldussüsteemid - tarkvara, millega abil saab luua andmebaas (mariaDB - XAMPP, SQL Server - SQL Server Management Studio)
- Andmebaas - struktureeritud andmete kogum
- Tabel - olem - сущности
- Veerg = väli - поле
- Rida = kirje - запись
- Primaarne võti - primary key -PK- veerg, unikaalse identifikatooriga (tavaliselt nimetus id)
- Välisvõti (võõrvõti) - foreign key - FK - veerg, mis loob seose teise tabeli primaarne võtmega

## SQL - structured quary language - struktureeritud päringu keel
  - päring - запрос 
  - <img width="427" height="339" alt="image" src="https://github.com/user-attachments/assets/e51d1e1c-af45-4551-81ff-fd6b12467944" />
  1. DDL - Data Definition Language
  2. DML - Data Manipulation Language

     ## Piirangud - органичения - CONSTRAINT (5)
     1. PRIMARY KEY
     2. NOT NULL
     3. CHECK - valik
     4. 
     ## Andmetüübid
     ```
     1. int, smallint, decimal(5,2) - numbrilised
     2. varchar(30), char(5), TEXT - tekst/sümbolised
     3. date, time, datetime - kuupäev
     4. boolean, bit, bool - loogilised
     ```
     
## Tabelivahelised seosed
- üks-ühele (nt naine-mees)
- üks-mitmele (nt naine -lapsed) <img width="804" height="468" alt="{0DE07821-8815-4A34-956F-5B67DA6A696B}" src="https://github.com/user-attachments/assets/3c032f19-5fcd-4b3e-9b90-0d52a4c01880" />

- mitme-mitmele (õpilased-tunnid)
- <img width="1017" height="659" alt="{C9AC0175-1F12-4680-B658-29736758917D}" src="https://github.com/user-attachments/assets/c0d6a859-bcf4-4ce5-b241-f93481fce6c3" />

## ALTER TABLE
``` sql
--tabeli struktuuri muutmine
--1. uue veeru lisamine
ALTER TABLE tootaja ADD testVeerg int;
Select * from tootaja;
--2. veeru kustutamine
ALTER TABLE tootaja DROP COLUMN testVeerg;
--3. andmetüübi muutmine veerus
ALTER TABLE tootaja ALTER COLUMN testVeerg varchar(5);
--struktuuri kontrollimiseks kasutame protseduur sp_help
sp_help tootaja; 
```

```sql
-- 1. ja 2. Tabelite loomine koos piirangutega
CREATE TABLE Category(
idCategory int PRIMARY KEY identity(1,1),
Category_Name varchar(50) not null UNIQUE)

CREATE TABLE Productt(
idProduct int PRIMARY KEY identity(1,1),
ProductName varchar(100) not null,
idCategory int,
Price decimal(10,2) CHECK (Price > 0),
FOREIGN KEY (idCategory) REFERENCES Category(idCategory))

CREATE TABLE Customer(
idCustomer int PRIMARY KEY identity(1,1),
Name varchar(100) not null,
Contact varchar(100))

CREATE TABLE Sale(
idSale int PRIMARY KEY identity(1,1),
idProductt int,
idCustomer int,
Count_pr int DEFAULT 1 CHECK (Count_pr > 0),
Date_of_sale date,
FOREIGN KEY (idProductt) REFERENCES Productt(idProductt),
FOREIGN KEY (idCustomer) REFERENCES Customer(idCustomer))

-- 3. Muuda mingi välja tüüpi
ALTER TABLE Category ALTER COLUMN Category_Name varchar(100);

-- 4. Lisa tabelisse Sale väli Units
ALTER TABLE Sale ADD Units varchar(10);

-- 5. Eemalda mingi piirang
-- Eemaldame unikaalsuse piirangu Category tabelist
ALTER TABLE Category DROP CONSTRAINT UQ__Category__3214EC06; 
-- (Märkus: MS SQL määrab UNIQUE piirangule nime automaatselt, kui seda ise ei nimeta)

-- Kontrollimiseks
SELECT * FROM Category;
SELECT * FROM Productt;
SELECT * FROM Customer;
SELECT * FROM Sale;
```
