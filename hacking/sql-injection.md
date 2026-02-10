# sql injection

\
SQL INJECTION:

<br>

## ze 3 explotazio egin dugu:

#### 1️⃣ SQL Injection sinplea — autentifikazioa / bilaketa apurtzea

Explotazioa:

' OR '1'='1

<br>

Zer gertatzen da?\
SQL kontsulta honela geratzen da:

SELECT id, username FROM usuarios WHERE username = '' OR '1'='1'

<br>

'1'='1' beti egia denez:

* Erabiltzaile guztiak bueltatzen dira\
  <br>
* Bilaketa edo autentifikazioa guztiz apurtzen da

#### 2️⃣ SQL Injection bidez erregistro konkretu bat lortzea (ID bidez)

Explotazioa:

' OR id=100 -- -

<br>

Zer gertatzen da?

* Erasotzaileak nahi duen erabiltzailearen datuak eskuratzen ditu\
  <br>
* Aplikazioak ez lukeen informazioa erakusten du\
  <br>

Zer frogatzen du?\
✔️ Datu zehatzak eskuratu daitezkeela\
✔️ Kontrolik gabe datu sentikorrak agerian geratzen direla

#### 3️⃣ SQL Injection + Stored XSS (kate-erasoa)

Explotazioa:

1. SQL Injection erabiliz, XSS payload-a duen erabiltzailea lortzen da:\
   <br>

' OR id=101 -- -

<br>

2. Erregistro horrek XSS kodea dauka (\<img onerror=...>)\
   <br>
3. Frontend-ean innerHTML erabiltzen denez:\
   <br>

* JavaScript exekutatzen da\
  <br>
* Alert-a, fondoaren aldaketa edo input-aren erregistroa gertatzen da\
  <br>

Zer frogatzen du?\
✔️ SQL Injection eta XSS elkarren artean kateatu daitezkeela\
✔️ Datu-baseko edukia exekuzio-kode bihurtzen dela\
✔️ Erasoaren inpaktua asko handitzen dela

<br>

### Zergatik da ahula kode hau?

Arazo nagusia erabiltzailearen sarrera zuzenean SQL kontsultan sartzen delako, inolako babesik gabe.

1️Erabiltzaileak nahi duena idatz dezake

HTML-n:

\<input type="text" id="search" placeholder="' OR '1'='1">

<br>

Hemen erabiltzaileak edozein testu sar dezake, baita SQL kodea ere.

***

2️ Balioa PHPra iristen da filtratu gabe

PHP-n:

$q = $\_POST\['q'] ?? '';

<br>

Hemen:

* &#x20;Ez da balioa garbitzen\
  <br>
* &#x20;Ez da balioa balioztatzen\
  <br>
* &#x20;Ez da prestatutako kontsultarik erabiltzen\
  <br>

Beraz, erabiltzaileak bidaltzen duena bere horretan erabiltzen da.

***

3️ Kontsulta SQL zuzenean eraikitzen da

Kode hau da arazoaren muina:

$sql = "SELECT id, username FROM usuarios WHERE username = '$q'";

<br>

Hau esan nahi du:

* $q-k SQL kodea badu → SQL zerbitzariak exekutatuko du\
  <br>
* PHPk ez du bereizten datua eta kodea\
  <br>

***

4️ SQL Injection adibidea

Erabiltzaileak hau sartzen badu:

' OR '1'='1

<br>

Sortzen den SQL kontsulta:

SELECT id, username FROM usuarios WHERE username = '' OR '1'='1'

<br>

&#x20;'1'='1' beti egia denez:

* Erabiltzaile guztiak bueltatzen ditu\
  <br>
* Autentifikazioa edo bilaketa guztiz apurtzen da\
  <br>

***

5️ Zergatik da hau arriskutsua?

Hau posible da:

* Datu guztiak ikustea\
  <br>
* Beste taulak kontsultatzea\
  <br>
* Pasahitzak lapurtzea\
  <br>
* DB ezabatzea (DROP TABLE)\
  <br>
* Sistema osoa konprometitzea\
  <br>

Eta gainera:

ini\_set('display\_errors', 1);

error\_reporting(E\_ALL);

<br>

Honek:

* x SQL errore zehatzak erakusten ditu\
  <br>
* x Erasotzaileari informazio gehiago ematen dio\
  <br>

GURE WEBGUNEAN  Bulnerabilitate bat aurkitu dugu eta explotatu dugu\
\
\
<br>

<figure><img src="../.gitbook/assets/unknown (4).png" alt=""><figcaption></figcaption></figure>

<br>
