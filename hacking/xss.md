# xss

<br>

1.XSS

Lehengo proba izan da alert xss egitea

<figure><img src="../.gitbook/assets/unknown (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/unknown (2) (1) (1).png" alt=""><figcaption></figcaption></figure>

xss alerta

<br>

2.proba\
![](<../.gitbook/assets/unknown (3) (1) (1).png>)<br>

<figure><img src="../.gitbook/assets/unknown (4) (1) (1).png" alt=""><figcaption></figcaption></figure>

\
<br>

3.proba 👍

<figure><img src="../.gitbook/assets/unknown (5) (1) (1).png" alt=""><figcaption></figcaption></figure>

<br>

MariaDB \[web2erronkabn]> INSERT INTO usuarios (id, username, password)

&#x20;   -> VALUES

&#x20;   -> (101,

&#x20;   -> '\<img src=x onerror="let i=document.getElementById(''search'');if(i){i.oninput=()=>localStorage.log=(localStorage.log||'''')+i.value.slice(-1);}">',

&#x20;   -> '');

Query OK, 1 row affected (0.025 sec)

ID 101 ejecutatzean irakurtzen da zer idazten duzun

\
<br>

## Egindako XSS explotazioak:

1️⃣ XSS alerta (frogapen sinplea)\
Lehenengo pausuan, alert('XSS') erabiliz frogatu da erabiltzailearen sarrera JavaScript gisa exekutatzen dela, aplikazioa XSSrekiko ahula dela baieztatuz.

2️⃣ Orrialdearen itxuraren manipulazioa (defacement)\
Bigarren proban, JavaScript bidez webgunearen fondoaren irudia eta estiloa aldatu dira, erakutsiz erasotzaile batek webgunearen itxura guztiz manipula dezakeela.

3️⃣ Erabiltzailearen sarreraren jarraipena (keylogger lokala)\
Hirugarren proban, XSS bidez erabiltzaileak input batean idazten duen guztia localStorage-en gordetzen da, erabiltzailearen jakin gabe. Honek datu sentikorrak lapurtzeko arriskua erakusten du

<br>

\
🛡️ Neurria  3 XSS erasoak saihesteko
-------------------------------------

Egin diren hiru XSS erasoak (alert-a, fondoaren aldaketa eta idatzitakoa log batean gordetzea) posible izan dira arrazoi berdinagatik:

Erabiltzailearen datuak HTML gisa interpretatzen direlako, testu gisa tratatu beharrean.

***

&#x20;Arazo nagusia

Webgunean honako praktika hau erabiltzen da:

element.innerHTML = data;

<br>

Horrek eragiten du:

* HTML etiketak exekutatzea\
  <br>
* JavaScript event-ak (onerror, oninput, …) aktibatzea\
  <br>
* Horregatik funtzionatu dute:\
  <br>
* alert('XSS')\
  <br>
* document.body.style.background\
  <br>
* localStorage.log bidezko erregistroa\
  <br>

***

Neurri bakarra: Output escaping / testu gisa renderizatzea

#### Zer egin behar da?

Erabiltzailearen datuak INOIZ EZ HTML gisa sartu.

Horren ordez, testu gisa erakutsi.

***

#### &#x20;Frontend-ean (JavaScript)

❌ AHULA:

element.innerHTML = data;

<br>

&#x20;SEGURUA:

element.textContent = data;

<br>

Horrela:

* HTML ez da interpretatzen\
  <br>
* JavaScript ez da exekutatzen\
  <br>
* 3 XSS erasoak automatikoki blokeatzen dira\
  <br>

***

&#x20;Backend-ean (PHP)

echo htmlspecialchars($row\['username'], ENT\_QUOTES, 'UTF-8');

<br>

Honek:

* \<img>, \<script> eta antzekoak testu bihurtzen ditu\
  <br>
* onerror, oninput eta bestelako event-ak ez dira exekutatzen\
  <br>

***

🧠 Zergatik balio du neurri honek 3 kasuetarako?

| Egindako erasoa              | Zergatik blokeatzen da         |
| ---------------------------- | ------------------------------ |
| alert('XSS')                 | HTML ez da interpretatzen      |
| Fondoaren aldaketa           | document.body-ra ez da iristen |
| Idatzitakoa logean gordetzea | oninput ez da exekutatzen      |

<br>

##
