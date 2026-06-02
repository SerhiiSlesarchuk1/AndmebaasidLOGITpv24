[<img src="https://img.shields.io/badge/🏠_Pealeht-README-gray?style=flat" />](README.md) [<img src="https://img.shields.io/badge/🔹_SQL_Kood-Code.sql-blue?style=flat" />](Code.md) [<img src="https://img.shields.io/badge/🔹_SQL_Kood_2.0-Code2.0.sql-blue?style=flat" />](Code2.0.md) [<img src="https://img.shields.io/badge/🔸_Juhend-CREATE_INSERT-orange?style=flat" />](CREATE_IMSERT.md) [<img src="https://img.shields.io/badge/🟩_Kasutajad-Kasutaja.md-green?style=flat" />](Kasutaja.md) [<img src="https://img.shields.io/badge/🟪_Müük-sales.md-teal?style=flat" />](sales.md) [<img src="https://img.shields.io/badge/🟥_Päästikud_(MySQL)-Triger.md-red?style=flat" />](Triger.md) [<img src="https://img.shields.io/badge/🟥_Päästikud_(XAMPP)-TrigerXAMMP.md-red?style=flat" />](TrigerXAMMP.md) [<img src="https://img.shields.io/badge/🟪_Protseduurid-Protseduurid.md-purple?style=flat" />](Protseduurid.md) [<img src="https://img.shields.io/badge/⬛_Salvestatud-Stored.md-black?style=flat" />](Stored.md)
--
# STORED

```sql
CREATE Database SlesarchukLOGpv24

--tabel klient
CREATE TABLE klient(
id int IDENTITY(1,1) PRIMARY KEY,
nimi NVARCHAR(100),
linn NVARCHAR(100),
vanus int,
saldo DECIMAL(10,2))
```

```sql
--1 Kuva kliendid
CREATE PROCEDURE sp_KuvaKliendid

@usslinn varchar(30)
AS
BEGIN
    SELECT nimi, linn
    FROM klient;
END;

-- Käivitamine
EXEC sp_KuvaKliendid @usslinn='Tallinn';
```

```sql
--2 Lisa klient
CREATE PROCEDURE sp_LisaKlient
@nimi NVARCHAR(100),
@linn NVARCHAR(100),
@vanus int,
@saldo DECIMAL(10,2)
AS
BEGIN
    INSERT INTO klient (nimi, linn, vanus, saldo)
    VALUES (@nimi, @linn, @vanus, @saldo);
END;

-- Käivitamine
EXEC sp_LisaKlient 
@nimi='Robert Maasikas',
@linn='Tallinn',
@vanus=20,
@saldo=170.50;

SELECT * FROM klient
```

```sql
--3 Muuda kliendi andmeid
CREATE PROCEDURE sp_MuudaKlient
@id int,
@linn NVARCHAR(100),
@saldo DECIMAL(10,2)
AS
BEGIN
    UPDATE klient
    SET linn=@linn,
        saldo=@saldo
    WHERE id=@id;
END;

-- Käivitamine
EXEC sp_MuudaKlient 
@id=1,
@linn='Tartu',
@saldo=300.00;
```

```sql
--4 Kustuta klient
CREATE PROCEDURE sp_KustutaKlient
@id int
AS
BEGIN
    DELETE FROM klient
    WHERE id = @id;
END;

-- Käivitamine
EXEC sp_KustutaKlient @id=2;
```

```sql
-- 5 Otsi klienti
CREATE PROCEDURE sp_OtsiKlient
@otsing NVARCHAR(100)
AS
BEGIN
    SELECT * FROM klient
    WHERE nimi LIKE @otsing+'%';
END;

-- Käivitamine
EXEC sp_OtsiKlient @otsing='M';
```

```sql
-- 6. Saldo min/max

CREATE PROCEDURE sp_SaldoMinMax
@minSaldo DECIMAL(10,2) OUTPUT,
@maxSaldo DECIMAL(10,2) OUTPUT
AS
BEGIN
    SELECT 
        @minSaldo=MIN(saldo),
        @maxSaldo=MAX(saldo)
    FROM klient;
END;

-- Käivitamine
DECLARE @min DECIMAL(10,2);
DECLARE @max DECIMAL(10,2);

EXEC sp_SaldoMinMax 
@min OUTPUT,
@max OUTPUT;

PRINT 'Min saldo: ' + CAST(@min AS NVARCHAR);
PRINT 'Max saldo: ' + CAST(@max AS NVARCHAR);
```

```sql
-- 7. Tingimuslause kasutamine (CASE / IF)

CREATE PROCEDURE sp_KliendiStaatus
AS
BEGIN
    SELECT 
        nimi,
        saldo,
        CASE
            WHEN saldo > 100 THEN 'Hea klient'
            ELSE 'Tavaklient'
        END AS staatus
    FROM klient;
END;

-- Käivitamine
EXEC sp_KliendiStaatus;
```

```sql
-- 8. Veeru haldus

CREATE PROCEDURE sp_VeeruHaldus
    @tegevus NVARCHAR(10)
AS
BEGIN
    DECLARE @sql NVARCHAR(MAX);

    IF @tegevus = 'LISA'
        SET @sql = 'ALTER TABLE klient ADD email NVARCHAR(100);';

    ELSE IF @tegevus = 'KUSTUTA'
        SET @sql = 'ALTER TABLE klient DROP COLUMN email;';

    EXEC sp_executesql @sql;
END;

-- Veeru lisamine
EXEC sp_VeeruHaldus @tegevus='LISA';
```
