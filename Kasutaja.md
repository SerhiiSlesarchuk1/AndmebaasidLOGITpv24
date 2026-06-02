[<img src="https://img.shields.io/badge/🏠_Pealeht-README-gray?style=flat" />](README.md) [<img src="https://img.shields.io/badge/🔹_SQL_Kood-Code.sql-blue?style=flat" />](Code.md) [<img src="https://img.shields.io/badge/🔹_SQL_Kood_2.0-Code2.0.sql-blue?style=flat" />](Code2.0.md) [<img src="https://img.shields.io/badge/🔸_Juhend-CREATE_INSERT-orange?style=flat" />](CREATE_IMSERT.md) [<img src="https://img.shields.io/badge/🟩_Kasutajad-Kasutaja.md-green?style=flat" />](Kasutaja.md) [<img src="https://img.shields.io/badge/🟪_Müük-sales.md-teal?style=flat" />](sales.md) [<img src="https://img.shields.io/badge/🟥_Päästikud_(MySQL)-Triger.md-red?style=flat" />](Triger.md) [<img src="https://img.shields.io/badge/🟥_Päästikud_(XAMPP)-TrigerXAMMP.md-red?style=flat" />](TrigerXAMPP.md) [<img src="https://img.shields.io/badge/🟪_Protseduurid-Protseduurid.md-purple?style=flat" />](Protseduurid.md) [<img src="https://img.shields.io/badge/⬛_Salvestatud-Stored.md-black?style=flat" />](Stored.md)
--
# KASUTAJA

<img width="707" height="649" alt="{53DAD221-5E4A-4BD5-A534-227D6B357D90}" src="https://github.com/user-attachments/assets/e407e652-65d8-4bf7-bea7-7f026046e143" />
<img width="714" height="658" alt="{80A2B49C-1570-495F-9E81-F74B78A98AC6}" src="https://github.com/user-attachments/assets/15c8a7de-48ba-4b17-8b87-e0b295084a33" />

```sql
create database SerhiiLOGITpv24
use SerhiiLOGITpv24;

Create table opilane(
opilaneId int primary key identity(1,1),
nimi varchar(30) not null,
vanus int,
aadress text);
Insert into opilane(nimi, vanus, aadress)
values('Suvi Talv', 22, 'Eesti, Tallinn')

select * from opilane;

grant select on opilane to serhii;
grant insert on opilane to serhii;
grant update on opilane to serhii;

Update opilane Set nimi='test' where opilaneId=1;

create table test(id int)

delete from opilane where opilaneId=1;
```
