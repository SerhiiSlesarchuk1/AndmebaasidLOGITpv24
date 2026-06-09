[<img src="https://img.shields.io/badge/🏠_Pealeht-README-gray?style=flat" />](README.md) [<img src="https://img.shields.io/badge/🔸_Juhend-CREATE_INSERT-orange?style=flat" />](CREATE_IMSERT.md) [<img src="https://img.shields.io/badge/🟩_Kasutajad-Kasutaja.md-green?style=flat" />](Kasutaja.md) [<img src="https://img.shields.io/badge/🟪_Veebipood-sales.md-teal?style=flat" />](sales.md) [<img src="https://img.shields.io/badge/🟥_Päästikud_(MySQL)-Triger.md-red?style=flat" />](Triger.md) [<img src="https://img.shields.io/badge/🟥_Päästikud_(XAMPP)-TrigerXAMMP.md-red?style=flat" />](TrigerXAMMP.md) [<img src="https://img.shields.io/badge/🟪_Protseduurid-Protseduurid.md-purple?style=flat" />](Protseduurid.md) [<img src="https://img.shields.io/badge/🟥_Keys (MySQL)-Keys.md-red?style=flat" />](Keys.md)
--

# 1. Primary Key (Primaarvõti)
## Definitsioon
Tuvastab unikaalselt iga rea tabelis. Ei tohi sisaldada NULL väärtusi ega korduvaid andmeid. Tabelil saab olla ainult üks primaarvõti.

<img width="310" height="153" alt="{B56DB0DF-ACA3-413C-A61A-045E926563E9}" src="https://github.com/user-attachments/assets/f04d85ee-21fd-4097-9078-fab1c992935e" />
<img width="181" height="83" alt="{F98474E3-AF2A-4DE7-B4D7-2EFFB65D180A}" src="https://github.com/user-attachments/assets/7c1e7975-7fd7-417c-a211-0b671fd96c79" />


# 2. Foreign Key (Välisvõti)
## Definitsioon
Väli või väljade kogum, mis viitab teise tabeli primaarvõtmele. See loodab seose tabelite vahel ja tagab viidatava terviklikkuse.

<img width="572" height="158" alt="{3972784B-7B20-405C-9F3D-A786E66F0748}" src="https://github.com/user-attachments/assets/6de6d107-f9ec-479f-9d8d-3baf101ce19c" />
<img width="237" height="268" alt="{E9EF4717-09B6-4FCA-B076-9452874E9E7C}" src="https://github.com/user-attachments/assets/ec929722-3241-4cd2-a49b-b6ec111726a0" />


# 3. Unique Key (Unikaalne võti)
## Definitsioon
Tagab, et kõik väärtused veerus on unikaalsed. Erinevalt primaarvõtmest võib see sisaldada NULL väärtust ja ühes tabelis võib olla mitu unikaalset võtit.

<img width="327" height="144" alt="{42EE10E5-18BB-4029-8C41-15A4DF0B3ED0}" src="https://github.com/user-attachments/assets/dc58066e-db0f-4aa1-a586-a161231fc181" />
<img width="221" height="101" alt="{18F59487-A938-420F-A90B-96AEE05ABC30}" src="https://github.com/user-attachments/assets/7c8124fe-6a56-46a4-97e1-bf65244ecb9a" />


# 4. Simple Key (Lihtvõti)
## Definitsioon
Võti, mis koosneb ainult ühest ainukesest veerust.

<img width="498" height="126" alt="{F30F58F4-7AFA-498C-BDFB-082C2DF2FABD}" src="https://github.com/user-attachments/assets/6835b85c-fe91-4c6a-a2dc-4f56937da2f9" />
<img width="195" height="84" alt="{DEFC322F-E75F-470C-9AA7-6A88846EC8F0}" src="https://github.com/user-attachments/assets/7d628dcb-6342-4a8e-9b60-2dab3e2cab64" />


# 5. Composite Key (Liitvõti)
## Definitsioon
Võti, mis koosneb kahest või enamast veerust. Seda kasutatakse siis, kui üksik veerg ei taga rea unikaalsust.

<img width="614" height="171" alt="{9564AB00-12D7-4EA2-9CAE-124E4282E076}" src="https://github.com/user-attachments/assets/5ebf0fdc-01fb-45dd-8eb0-2bff774e8270" />
<img width="236" height="116" alt="{F27B1063-7967-4A4E-ABB1-D4C08E5D60F8}" src="https://github.com/user-attachments/assets/0f2823c6-5e2d-4891-92a2-6eca663e1c3d" />


# 6. Compound Key (Kombineeritud liitvõti)
## Definitsioon
Liitvõtme alamliik, kus vähemalt üks võtme koostisosadest on ühtlasi ka välisvõti (Foreign Key), mis viitab teisele tabelile.

<img width="463" height="190" alt="{91E40317-48A6-4EC3-A070-A18584A2B183}" src="https://github.com/user-attachments/assets/3eaa2681-0a0e-4086-8478-8a1149c3cec0" />
<img width="257" height="251" alt="{32418B42-9CD7-4CBC-8D98-A56C143D5DDC}" src="https://github.com/user-attachments/assets/8c2bbd3d-cb3f-4740-b342-6a77f911ea85" />


# 7. Superkey (Supervõti)
## Definitsioon
Mis tahes veergude kombinatsioon, mis võimaldab tabeli rida unikaalselt tuvastada. Võib sisaldada üleliigseid veerge (andmeid, ilma milleta oleks rida ikkagi unikaalne).

<img width="480" height="146" alt="{48EDCA81-6811-4A3A-83AD-C161D287DA4F}" src="https://github.com/user-attachments/assets/23923e5a-f392-45ad-9528-cfa06a8dbe72" />


# 8. Candidate Key (Kandidaatvõti)
## Definitsioon
Minimaalne supervõti. Veergude hulk, mis tuvastab rea unikaalselt, kuid millest ei saa eemaldada ühtegi veergu ilma, et unikaalsus kaoks (puudub ülemäärasus). Kandidaatvõtmete seast valitakse üks Primary Key.

<img width="484" height="148" alt="{CF4E5597-B505-41DD-B062-116EC548A154}" src="https://github.com/user-attachments/assets/0f8d40b2-036b-41d9-9dcf-1e83ad9a52c6" />
<img width="218" height="133" alt="{B28894A4-CBF3-409F-A751-FD33EE947940}" src="https://github.com/user-attachments/assets/8379cab1-43bb-4a9a-aa16-71a39af06b97" />


# 9. Alternate Key (Alternatiivvõti)
## Definitsioon
Kandidaatvõti, mida ei valitud tabeli primaarvõtmeks. Seda nimetatakse sageli ka sekundaarseks võtmeks.

<img width="673" height="145" alt="{85EC93C1-EED8-4B49-B8BA-CB4E6A96FEAC}" src="https://github.com/user-attachments/assets/d11b45c2-fa20-4440-82d9-87f2a8ddfc25" />
<img width="233" height="113" alt="{7C395C22-33AA-4662-A91A-7BB0CD1C8B3B}" src="https://github.com/user-attachments/assets/588531f7-9c43-4142-9d44-bb108015b6c9" />


# Rohkem infot SQL-i ja andmebaaside struktuuri kohta leiad siit
## Info Link
[SQL Database Keys](https://www.w3schools.com/sql/)
