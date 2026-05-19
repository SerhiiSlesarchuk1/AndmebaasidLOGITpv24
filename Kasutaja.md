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
