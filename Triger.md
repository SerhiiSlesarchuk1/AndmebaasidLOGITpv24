[<img src="https://img.shields.io/badge/🏠_Pealeht-README-gray?style=flat" />](README.md) [<img src="https://img.shields.io/badge/🔹_SQL_Kood-Code.sql-blue?style=flat" />](Code.md) [<img src="https://img.shields.io/badge/🔹_SQL_Kood_2.0-Code2.0.sql-blue?style=flat" />](Code2.0.md) [<img src="https://img.shields.io/badge/🔸_Juhend-CREATE_INSERT-orange?style=flat" />](CREATE_IMSERT.md) [<img src="https://img.shields.io/badge/🟩_Kasutajad-Kasutaja.md-green?style=flat" />](Kasutaja.md) [<img src="https://img.shields.io/badge/🟪_Müük-sales.md-teal?style=flat" />](sales.md) [<img src="https://img.shields.io/badge/🟥_Päästikud_(MySQL)-Triger.md-red?style=flat" />](Triger.md) [<img src="https://img.shields.io/badge/🟥_Päästikud_(XAMPP)-TrigerXAMMP.md-red?style=flat" />](TrigerXAMMP.md) [<img src="https://img.shields.io/badge/🟪_Protseduurid-Protseduurid.md-purple?style=flat" />](Protseduurid.md) [<img src="https://img.shields.io/badge/⬛_Salvestatud-Stored.md-black?style=flat" />](Stored.md)
--
# Trigger SQL

```sql
create database serhiiSlesarchuk
use serhiiSlesarchuk

CREATE TABLE linnad(
linnId int primary key identity(1,1),
linnanimi varchar(30) unique,
maakond varchar(50),
rahvaarv int);
select * from linnad;
INSERT INTO linnad(linnanimi, maakond, rahvaarv)
VALUES ('Tallinn', 'Harjumaa', 600000);

--tabel logi - tabel, mis täidab triger, kui kasutaja täidab tabeli linnad!
CREATE TABLE logi(
id int primary key identity(1,1),
kasutaja varchar(50),
aeg DATETIME,
andmed TEXT);

--1. Triger lisatud andmete jälgimeseks tabelis linnad.
--jälgib linna sisestamine tabelisse ja teeb vastava kirje logi-tabelis
CREATE TRIGGER linnaLisamine
ON linnad -- tabel, mida triger jälgib
FOR INSERT
AS
INSERT INTO logi(kasutaja, aeg, andmed)
SELECT
SYSTEM_USER, --siselogitud user
GETDATE(),
CONCAT('lisatud: ',inserted.linnanimi,', ',
inserted.maakond,', ',inserted.rahvaarv)
FROM inserted;

--kontrollimiseks tuleb lisada linna tabelisse linnad
INSERT INTO linnad(linnanimi, maakond, rahvaarv)
VALUES ('Viljandi', 'Viljandimaa', 50000);

SELECT * FROM linnad;
SELECT * FROM logi;

--2. DELETE triger - jälgib kustutamine tabelis linnad
--ja teeb vastava kirje logi tabelisse
CREATE TRIGGER linnaKustutamine
ON linnad -- tabel, mida triger jälgib
FOR DELETE
AS
INSERT INTO logi(kasutaja, aeg, andmed)
SELECT
SYSTEM_USER, --siselogitud user
GETDATE(),
CONCAT('kustutatud: ',deleted.linnanimi,', ',
deleted.maakond,', ',deleted.rahvaarv)
FROM deleted;

--DISABLE TRIGGER ....
DISABLE TRIGGER linnakustutamine ON linnad;
ENABLE TRIGGER linnaKustutamine ON linnad;

--DELETE trigeri kontroll
DELETE FROM linnad WHERE linnId=2;
select * from linnad
select * from logi;

CREATE TRIGGER LinnaLisaKustumine
```
