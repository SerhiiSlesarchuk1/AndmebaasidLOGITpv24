## AndmebaasidLOGITpv24
admebaaside haldusega seotud sql kood ja konspektid

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

