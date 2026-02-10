# SEA

Sistema eragile desberdinen artean baliabideak partekatzearen beharra azaldu da Erabili beharreko tresnak justifikatu dira

<br>

Punkets eta Kutxabank enpresen fusioaren ondorioz, departamentu desberdinek sistema eragile ezberdinetako baliabideak partekatu behar dituzte. Administrazioak Punkets-eko Windows Server erabiltzen du, eta garapenak Linux Ubuntu. DFS Windows Server-en erabiliz eta Ubuntu-n  Samba-Webmin bidez, erabiltzaile guztiek fitxategi berberetara sarbidea izango dute, segurtasuna eta konsistentzia bermatuz.

<br>

Ondoko komandotatik denak egin dira

<br>

1️⃣-Erabiltzaile bat sortu OU baten barruan eta pasahitza eskatuta

<figure><img src="../.gitbook/assets/unknown (1) (1).png" alt=""><figcaption></figcaption></figure>

2️⃣-Bi erabiltzaile OU batetik bestera mugitu

1.Erabiltzailea

<figure><img src="../.gitbook/assets/unknown (2) (1).png" alt=""><figcaption></figcaption></figure>

2.erabiltzailea

<figure><img src="../.gitbook/assets/unknown (3) (1).png" alt=""><figcaption></figcaption></figure>

3️⃣- Erabiltzaile bi talde batetik atera

<br>

Oskar erabiltzaileak inprimagailu taldean daude

<figure><img src="../.gitbook/assets/unknown (4) (1).png" alt=""><figcaption></figcaption></figure>

Taldetik kampo

<figure><img src="../.gitbook/assets/unknown (5) (1).png" alt=""><figcaption></figcaption></figure>

4️⃣ -Erabiltzaile bi talde baten sartu

<figure><img src="../.gitbook/assets/unknown (6) (1).png" alt=""><figcaption></figcaption></figure>

5️⃣- OU bat kokapen batetik bestera mugitu

<br>

<figure><img src="../.gitbook/assets/unknown (7) (1).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/unknown (8) (1).png" alt=""><figcaption></figcaption></figure>

6️⃣ -Talde baten barruan dauden erabiltzaileen zerrenda atera

<figure><img src="../.gitbook/assets/unknown (9) (1).png" alt=""><figcaption></figcaption></figure>

7️⃣ -Izenean testu jakin bat daukaten taldeak zerrendatu

<figure><img src="../.gitbook/assets/unknown (10) (1).png" alt=""><figcaption></figcaption></figure>

8️⃣- Globalak ez diren taldeak zerrendatu

<figure><img src="../.gitbook/assets/unknown (11) (1).png" alt=""><figcaption></figcaption></figure>

9️⃣- Erabiltzaile bat ezgaitu

<figure><img src="../.gitbook/assets/unknown (12) (1).png" alt=""><figcaption></figcaption></figure>

1️⃣0️⃣- Ezgaituta dauden erabiltzaileak zerrendatu

<figure><img src="../.gitbook/assets/unknown (13) (1).png" alt=""><figcaption></figcaption></figure>

1️⃣1️⃣- OU-en egitura zerrendatu

<figure><img src="../.gitbook/assets/unknown (14) (1).png" alt=""><figcaption></figcaption></figure>

\
<br>

Linux zerbitzarian baliabideak modu egokian partekatu dira&#x20;

Webmin linux\_partekatua izeneko karpeta bat sortu eta partekatu da

<figure><img src="../.gitbook/assets/unknown (15).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/unknown (16).png" alt=""><figcaption></figcaption></figure>

<br>

Linux zerbitzarian partekatutako baliabideeetan baimenak zuzen eman dira.

<br>

Hemen karpetaren baimena ikusi ahal da

<figure><img src="../.gitbook/assets/unknown (17).png" alt=""><figcaption></figcaption></figure>

Orain Active Directory sortu ditugun bezero bi webmin sortu ditugu, eta hauen pasahitza berdina ere.

<br>

1.erabiltzaile

<figure><img src="../.gitbook/assets/unknown (18).png" alt=""><figcaption></figcaption></figure>

2.erabiltzaile

<figure><img src="../.gitbook/assets/unknown (19).png" alt=""><figcaption></figcaption></figure>

Ondoren erabiltzaile hauek Samba erabiltzaileak bihurtu ditugu

<figure><img src="../.gitbook/assets/unknown (20).png" alt=""><figcaption></figcaption></figure>

Ondoren erabiltzaile hauek partekatu dugun karpetan baimena emango diogu

<figure><img src="../.gitbook/assets/unknown (21).png" alt=""><figcaption></figcaption></figure>

Linuxen partekatutako baliabidea DFS-ra gehitu da.

Ubuntun sortu dugun karpeta windows zerbitzariko DFS-an gehitu dugu.

<figure><img src="../.gitbook/assets/unknown (22).png" alt=""><figcaption></figcaption></figure>

Bezerero batetik DFSrako atzipena egoki egiten dela egiaztatu da

<br>

Bezero batetik sarean zerbitzariko dfs-an sartu gara, eta webmin partekatutako karpeta barruan sartu gara , bakarrik sartu ahal dira baimena dituzten erabiltzaileak kasu honeta Bryan eta Oier.

Dfs barrura sartzen

<figure><img src="../.gitbook/assets/unknown (23).png" alt=""><figcaption></figcaption></figure>

Ubuntuaren ip-arekin jartzen

<br>

<figure><img src="../.gitbook/assets/unknown (24).png" alt=""><figcaption></figcaption></figure>

<br>

Karpeten baimena ikusteko:

<br>

<figure><img src="../.gitbook/assets/unknown (25).png" alt=""><figcaption></figcaption></figure>

<br>
