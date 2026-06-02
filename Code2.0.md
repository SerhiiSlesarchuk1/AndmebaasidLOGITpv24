[<img src="https://img.shields.io/badge/🏠_Pealeht-README-gray?style=flat" />](README.md) [<img src="https://img.shields.io/badge/🔹_SQL_Kood-Code.sql-blue?style=flat" />](Code.md) [<img src="https://img.shields.io/badge/🔹_SQL_Kood_2.0-Code2.0.sql-blue?style=flat" />](Code2.0.md) [<img src="https://img.shields.io/badge/🔸_Juhend-CREATE_INSERT-orange?style=flat" />](CREATE_IMSERT.md) [<img src="https://img.shields.io/badge/🟩_Kasutajad-Kasutaja.md-green?style=flat" />](Kasutaja.md) [<img src="https://img.shields.io/badge/🟪_Müük-sales.md-teal?style=flat" />](sales.md) [<img src="https://img.shields.io/badge/🟥_Päästikud_(MySQL)-Triger.md-red?style=flat" />](Triger.md) [<img src="https://img.shields.io/badge/🟥_Päästikud_(XAMPP)-TrigerXAMMP.md-red?style=flat" />](TrigerXAMPP.md) [<img src="https://img.shields.io/badge/🟪_Protseduurid-Protseduurid.md-purple?style=flat" />](Protseduurid.md) [<img src="https://img.shields.io/badge/⬛_Salvestatud-Stored.md-black?style=flat" />](Stored.md)
--

# CodeSql2.0
```sql
--andmete uuendamine tabelis
UPDATE tootaja SET aadress='Tallinn', koormus=10, aktiivne=1
WHERE tootajaID=1;


Create Database SlesarchukLOGIpv24baas;

--ad kustutamine
DROP Database puhtejevTriger;

USE SlesarchukLOGIpv24baas;
CREATE TABLE tootaja(
tootajaID int PRIMARY KEY identity(1,1), --identity - automaatselt kasvav arv +1
eesnimi varchar(15) not null,
perenimi varchar(30) not null,
synniaeg date,
aadress TEXT,
koormus int CHECK (koormus>0), -- piirang, et koormus >0
aktiivne bit)

--tabeli kuvamine
SELECT * FROM tootaja;

--admete lisamine tabelisse
INSERT INTO tootaja(perenimi, eesnimi, synniaeg)
VALUES ('Ilus', 'Liis', '2008-10-25')

INSERT INTO tootaja
VALUES ('Leena', 'Punane', '2012-10-4', 'Tallinn', 120, 1)

INSERT INTO tootaja
VALUES ('Katja', 'Punane', '2012-10-4', 'Tartu', 120, 1),
('Petja', 'Runane', '2002-10-4', 'Narva', 200,0)

--andmete uuendamine tabelis
UPDATE tootaja SET aadress='Tallinn', koormus=10, aktiivne=1
WHERE tootajaID=1;

--teine tabel
CREATE TABLE toovahetus(
toovahetusID int PRIMARY KEY identity(1,1),
kuupaev date,
tundideArv int,
tootajaID int,
FOREIGN KEY (tootajaID) REFERENCES tootaja(tootajaID))

select * from toovahetus;
select * from tootaja;
select * from koolitus;
select * from opetamine;

--täidame tabeli
INSERT INTO toovahetus
VALUES ('2026-04-14', 10, 4)

CREATE TABLE koolitus(
koolitusID int PRIMARY KEY identity(1,1),
nimetus varchar(100) NOT NULL,
kestvus int,              -- длительность
algus date,
lopp date,
opetaja varchar(50));

CREATE TABLE opetamine(
opetamineID int PRIMARY KEY identity(1,1),
tootajaID int,
koolitusID int,
tunnistus bit,           -- сертификат
hinne int,               -- оценка
FOREIGN KEY (tootajaID) REFERENCES tootaja(tootajaID),
FOREIGN KEY (koolitusID) REFERENCES koolitus(koolitusID));

INSERT INTO koolitus (nimetus, kestvus, algus, lopp, opetaja)
VALUES ('SQL Alused', 40, '2026-03-01', '2026-03-10', 'Ivan Ivanov'),
('Turvalisus', 20, '2026-04-01', '2026-04-05', 'Maria Petrova');

INSERT INTO opetamine (tootajaID, koolitusID, tunnistus, hinne)
VALUES (5, 1, 1, 5),
(2, 1, 1, 4),
(1, 2, 0, 3);

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

--piirangute lisamine
CREATE TABLE ryhm(
ryhmId int not null,
ryhmNimi char (10));

DROP TABLE ryhm;
--muudame tabeli ja lisame priirang - primary key
ALTER TABLE ryhm ADD CONSTRAINT pk_ryhm PRIMARY KEY (ryhmId);

INSERT INTO ryhm 
VALUES (3, 'TITpe24');
SELECT * FROM ryhm;
--lisame piirang UNIQUE
ALTER TABLE ryhm ADD CONSTRAINT un_ryhm UNIQUE (ryhmNimi);

--lisame uus veerg
ALTER TABLE ryhm ADD ryhmajuhataja int;
--lisame piirang Foreign Key
ALTER TABLE ryhm ADD CONSTRAINT fk_ryhm 
FOREIGN KEY (ryhmajuhataja) REFERENCES tootaja(tootajaId);
--kontrollimiseks
SELECT * FROM tootaja;
SELECT * FROM ryhm;
UPDATE ryhm SET ryhmajuhataja=2 WHERE ryhmNimi='TITpe24';

-- 1 ja 2 Tabelite loomine koos piirangutega
CREATE TABLE Category(
idCategory int PRIMARY KEY identity(1,1),
Category_Name varchar(50) not null UNIQUE)
--Category (idCategory, Category_Name)

CREATE TABLE Productt(
idProductt int PRIMARY KEY identity(1,1),
ProductName varchar(100) not null,
idCategory int,
Price decimal(10,2) CHECK (Price > 0),
FOREIGN KEY (idCategory) REFERENCES Category(idCategory))
--Product (idProduct, Name, idCategory, Price)

CREATE TABLE Customer(
idCustomer int PRIMARY KEY identity(1,1),
Name varchar(100) not null,
Contact varchar(100))
--



-- 3. Muuda mingi välja tüüpi
ALTER TABLE Category ALTER COLUMN Category_Name varchar(100);

-- 4. Lisa tabelisse Sale väli Units
ALTER TABLE Sale ADD Units varchar(10);

-- 5. Eemalda mingi piirang
-- Eemaldame unikaalsuse piirangu Category tabelist
EXEC sp_help 'Category';
-- (Märkus: MS SQL määrab UNIQUE piirangule nime automaatselt, kui seda ise ei nimeta)

-- Kontrollimiseks
SELECT * FROM Category;
SELECT * FROM Productt;
SELECT * FROM Customer;
SELECT * FROM Sale;

--Tabel Sale
CREATE TABLE Sale(
idSale int PRIMARY KEY identity(1,1),
idProductt int,
idCustomer int,
FOREIGN KEY (idProductt) REFERENCES Productt(idProductt),
Count int,
date_of_sale date)
--Tabel Customer 
 CREATE TABLE Customer(
 idCustomer int PRIMARY KEY identity(1,1),
 Name varchar(100) not null,
 Contact varchar(100))
ALTER TABLE Sale ADD CONSTRAINT fk_sale 
FOREIGN KEY (idCustomer) REFERENCES Customer(idCustomer);

INSERT INTO Category  
VALUES ('autot')

INSERT INTO Productt
VALUES ('honda', 2, 750)

INSERT INTO Customer
VALUES ('Katja', '5344 4444')

INSERT INTO Sale
VALUES (2, 1, 10,'2006-10-10')

SELECT * FROM Sale;
SELECT * FROM Productt;
SELECT * FROM Customer;
SELECT * FROM Category;
```
