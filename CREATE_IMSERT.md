[<img src="https://img.shields.io/badge/🏠_Pealeht-README-gray?style=flat" />](README.md) [<img src="https://img.shields.io/badge/🔹_SQL_Kood-Code.sql-blue?style=flat" />](Code.md) [<img src="https://img.shields.io/badge/🔹_SQL_Kood_2.0-Code2.0.sql-blue?style=flat" />](Code2.0.md) [<img src="https://img.shields.io/badge/🔸_Juhend-CREATE_INSERT-orange?style=flat" />](CREATE_IMSERT.md) [<img src="https://img.shields.io/badge/🟩_Kasutajad-Kasutaja.md-green?style=flat" />](Kasutaja.md) [<img src="https://img.shields.io/badge/🟪_Müük-sales.md-teal?style=flat" />](sales.md) [<img src="https://img.shields.io/badge/🟥_Päästikud_(MySQL)-Triger.md-red?style=flat" />](Triger.md) [<img src="https://img.shields.io/badge/🟥_Päästikud_(XAMPP)-TrigerXAMMP.md-red?style=flat" />](TrigerXAMMP.md) [<img src="https://img.shields.io/badge/🟪_Protseduurid-Protseduurid.md-purple?style=flat" />](Protseduurid.md) [<img src="https://img.shields.io/badge/⬛_Salvestatud-Stored.md-black?style=flat" />](Stored.md)
--
--
# CREATE-INSERT
```sql
--andmete uuendamine tabelis
UPDATE tootaja SET aadress='Tallinn', koormus=10, aktiivne=1
WHERE tootajaID=1;
```

```sql
Create Database SlesarchukLOGIpv24baas;
```

```sql
--ad kustutamine
DROP Database puhtejevTriger;
```

```sql
USE SlesarchukLOGIpv24baas;
CREATE TABLE tootaja(
tootajaID int PRIMARY KEY identity(1,1), --identity - automaatselt kasvav arv +1
eesnimi varchar(15) not null,
perenimi varchar(30) not null,
synniaeg date,
aadress TEXT,
koormus int CHECK (koormus>0), -- piirang, et koormus >0
aktiivne bit)
```

```sql
--tabeli kuvamine
SELECT * FROM tootaja;
```

```
--admete lisamine tabelisse
INSERT INTO tootaja(perenimi, eesnimi, synniaeg)
VALUES ('Ilus', 'Liis', '2008-10-25')
```

```sql
INSERT INTO tootaja
VALUES ('Leena', 'Punane', '2012-10-4', 'Tallinn', 120, 1)
```

```sql
INSERT INTO tootaja
VALUES ('Katja', 'Punane', '2012-10-4', 'Tartu', 120, 1),
('Petja', 'Runane', '2002-10-4', 'Narva', 200,0)
```

```sql
--andmete uuendamine tabelis
UPDATE tootaja SET aadress='Tallinn', koormus=10, aktiivne=1
WHERE tootajaID=1;
```

```sql
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
```

```sql
--täidame tabeli
INSERT INTO toovahetus
VALUES ('2026-04-14', 10, 4)
```

```sql
CREATE TABLE koolitus(
koolitusID int PRIMARY KEY identity(1,1),
nimetus varchar(100) NOT NULL,
kestvus int,              -- длительность
algus date,
lopp date,
opetaja varchar(50));
```

```sql
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
```

```sql
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
```

```sql
--lisame uus veerg
ALTER TABLE ryhm ADD ryhmajuhataja int;
--lisame piirang Foreign Key
ALTER TABLE ryhm ADD CONSTRAINT fk_ryhm 
FOREIGN KEY (ryhmajuhataja) REFERENCES tootaja(tootajaId);
```

```sql
--kontrollimiseks
SELECT * FROM tootaja;
SELECT * FROM ryhm;
UPDATE ryhm SET ryhmajuhataja=4 WHERE ryhmNimi='LOGITpe24';
```
