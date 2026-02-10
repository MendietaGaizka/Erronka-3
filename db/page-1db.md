# Page 1DB

## &#x20;PUNKETS BANK – INDIZE AURRERATUAK ETA EGIAZTAPENA

### 1️ INDIZE KONPOSATUAK (Composite Index)

#### 📌 clientes taula – izena + emaila

CREATE INDEX idx\_clientes\_nombre\_email

ON clientes(nombre, email);

<br>

#### 🧠 Azalpena

Indize konposatu batek zutabe bat baino gehiago hartzen ditu.

#### ✅ Justifikazioa (errubrika maila altua)

* Bezeroak izenaren eta emailaren arabera bilatzen dira askotan\
  <br>
* Autentifikazio edo administrazio-kontsultak optimizatzen ditu\
  <br>
* Kontsulta konplexuetan errendimendua hobetzen du\
  <br>

***

#### 🔍 Egiaztapena

EXPLAIN

SELECT \* FROM clientes

WHERE nombre = 'Laura Gómez'

AND email = 'laura.gomez@mail.com';

<br>

➡ key: idx\_clientes\_nombre\_email agertu behar da

<figure><img src="../.gitbook/assets/unknown (61).png" alt=""><figcaption></figcaption></figure>

***

### 2️ UNIQUE INDEX (Datuen osotasuna)

#### 📌 clientes.dni

CREATE UNIQUE INDEX idx\_clientes\_dni

ON clientes(dni);

<br>

#### &#x20;Azalpena

UNIQUE INDEX batek balio errepikatuak saihesten ditu.

#### ✅ Justifikazioa

* DNI bakarra izan behar du bezero bakoitzak\
  <br>
* Datuen koherentzia bermatzen du\
  <br>
* Banku-ingurune batean derrigorrezkoa\
  <br>

***

#### 🔍 Egiaztapena

EXPLAIN

SELECT \* FROM clientes

WHERE dni = '12345678A';

<br>

<figure><img src="../.gitbook/assets/unknown (62).png" alt=""><figcaption></figcaption></figure>

***

### 3️ INDIZE KONPOSATUA – cuentas

#### 📌 bezeroa + saldoa

CREATE INDEX idx\_cuentas\_cliente\_saldo

ON cuentas(cliente\_id, saldo);

<br>

#### Azalpena

Bezero baten kontuak saldoaren arabera aztertzeko.

#### ✅ Justifikazioa

* Bezero baten kontu handienak bilatzeko\
  <br>
* Txosten finantzarioetan oso erabilia\
  <br>
* Errendimendua hobetzen du JOIN-ekin\
  <br>

***

#### 🔍 Egiaztapena

EXPLAIN

SELECT \* FROM cuentas

WHERE cliente\_id = 3

AND saldo > 10000;

<figure><img src="../.gitbook/assets/unknown (63).png" alt=""><figcaption></figcaption></figure>

<br>

***

### 4️ INDIZE KONPOSATUA – movimientos

#### 📌 kontua + data

CREATE INDEX idx\_movimientos\_cuenta\_fecha

ON movimientos(cuenta\_id, fecha);

<br>

#### &#x20;Azalpena

Kontu baten mugimenduak denbora-tarte batean bilatzeko.

#### ✅ Justifikazioa

* Auditoretzak\
  <br>
* Kontu-laburpenak\
  <br>
* Iruzur-detekzioa\
  <br>

Bankuetan hau oso kritikoa da.

***

#### 🔍 Egiaztapena

EXPLAIN

SELECT \* FROM movimientos

WHERE cuenta\_id = 1

AND fecha BETWEEN '2025-01-01' AND '2025-12-31';

<figure><img src="../.gitbook/assets/unknown (64).png" alt=""><figcaption></figcaption></figure>

***

### 5️ INDIZEA ENUM zutabean

#### 📌 mugimendu mota

CREATE INDEX idx\_movimientos\_tipo

ON movimientos(tipo);

<br>

#### &#x20;Azalpena

ENUM zutabeetan ere indizeak erabil daitezke.

#### ✅ Justifikazioa

* Deposituak / transferentziak bereizteko\
  <br>
* Txosten estatistikoak optimizatzeko\
  <br>
* Analisi azkarragoak\
  <br>

***

#### 🔍 Egiaztapena

EXPLAIN

SELECT \* FROM movimientos

WHERE tipo = 'TRANSFERENCIA';

<br>

***

### 6  INDIZEEN LABURPEN TAULA (DOKUMENTAZIORAKO IDEALA)

| Taula       | Indizea            | Helburua             |
| ----------- | ------------------ | -------------------- |
| clientes    | nombre, email      | Bilaketa konbinatua  |
| clientes    | dni (UNIQUE)       | Datuen osotasuna     |
| cuentas     | cliente\_id, saldo | Analisi finantzarioa |
| movimientos | cuenta\_id, fecha  | Auditoretza          |
| movimientos | tipo               | Estatistikak         |

👉 Hau memoria edo proiektuan zuzenean sartzeko modukoa da.

***

### 7 INDIZE GUZTIAK IKUSTEKO

SHOW INDEX FROM clientes;

SHOW INDEX FROM cuentas;

SHOW INDEX FROM movimientos;

### &#x20;EVENT AUTOMATIKOA

#### 🔹 Zer da EVENT bat?

EVENT bat MySQL-eko zereginen programatzailea da. Cron-en antzekoa da, baina datu-basearen barruan exekutatzen da.

***

#### 🔹 Sortutako EVENT-a

CREATE EVENT backup\_diario\_punkets

ON SCHEDULE EVERY 1 DAY

STARTS CURRENT\_TIMESTAMP

DO

BEGIN

&#x20;   DELETE FROM punketsdb\_backup.movimientos;

&#x20;   DELETE FROM punketsdb\_backup.cuentas;

&#x20;   DELETE FROM punketsdb\_backup.clientes;

&#x20;   DELETE FROM punketsdb\_backup.ceos;

<br>

&#x20;   INSERT INTO punketsdb\_backup.ceos

&#x20;       SELECT \* FROM punketsdb.ceos;

<br>

&#x20;   INSERT INTO punketsdb\_backup.clientes

&#x20;       SELECT \* FROM punketsdb.clientes;

<br>

&#x20;   INSERT INTO punketsdb\_backup.cuentas

&#x20;       SELECT \* FROM punketsdb.cuentas;

<br>

&#x20;   INSERT INTO punketsdb\_backup.movimientos

&#x20;       SELECT \* FROM punketsdb.movimientos;

END;

<br>

***

#### 🔹 Nola funtzionatzen du?

1. Egunero automatikoki exekutatzen da\
   <br>
2. Backup-eko taulak garbitzen ditu\
   <br>
3. Datu guztiak berriro kopiatzen ditu\
   <br>
4. Backup-a beti eguneratuta mantentzen du\
   <br>

***

#### 🔹 Zergatik egunero?

* Banku-datuak etengabe aldatzen dira\
  <br>
* Egun bateko datu-galera onargarria da (RPO = 24h)\
  <br>
* Errendimendu-kostua txikia da\
  <br>
