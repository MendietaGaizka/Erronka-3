# Page 1

Guia de HAproxy en pfSense

<br>

Instalar haproxy en System > Package Manager > Available Packages

<figure><img src=".gitbook/assets/unknown (51).png" alt=""><figcaption></figcaption></figure>

<br>

Después vete a Services > HAProxy > Backend y añade los servidores backend (el que tiene la web)

<figure><img src=".gitbook/assets/unknown (52).png" alt=""><figcaption></figcaption></figure>

<br>

Ponle nombre e IMPORTANTE en ‘Server List’ pon la IP de servidor que tiene la web, el puerto por el que se ve la web y en ‘Weight’ ponlo en 1 !!! segun gpt funciona si lo dejas vacio, pero a mi solo me ha funcionado cuando lo pongo en 1 !!!

<figure><img src=".gitbook/assets/unknown (53).png" alt=""><figcaption></figcaption></figure>

Obviamente dejalo en active ;)

\
\
\
\
<br>

Si tienes dos servidores web pon ‘Round robin’ si solo tienes uno como yo dejalo en ‘None’ ;)

<figure><img src=".gitbook/assets/unknown (54).png" alt=""><figcaption></figcaption></figure>

<br>

Elige HTTP. IMPORTANTE pon ‘Http check method’ en GET, por defecto esta OPTIONS y a mi eso no me ha funcionado. En ‘Url used by http check requests’ déjalo vacío o pon /

<figure><img src=".gitbook/assets/unknown (55).png" alt=""><figcaption></figcaption></figure>

\
<br>

Ahora que tienes hecho la parte de backend te hace falta poner el frontend champions ;)

<br>

Vete a Services > HAProxy > Frontend y añade la IP por la que se verá la web en este caso WAN para que el resto del mundo lo vea, tambien tienes que especificar el puerto (a tu gusto elegir el puerto ;). IMPORTANTE recuerda el puerto que elegiste que después tendras que añadir una regla.

<br>

<figure><img src=".gitbook/assets/unknown (56).png" alt=""><figcaption></figcaption></figure>

Obviamente dejalo en active crack ;)

<br>

IMPORTANTE Más abajo en ‘Actions’ elige ‘Use Backend’ y eliges el backend que creaste antes champion ;)

<figure><img src=".gitbook/assets/unknown (57).png" alt=""><figcaption></figcaption></figure>

\
\
\
\
\
\
\
<br>

Si has llegado hasta aquí significa que eres un verga larga y un putisimo chad ;)

Pero te habrás dado cuenta de que no funciona eso es porque no has activado el servicio campeón

<br>

Vete a Services > HAProxy > Settings y marca la casilla ‘Enable HAProxy’

<figure><img src=".gitbook/assets/unknown (58).png" alt=""><figcaption></figcaption></figure>

<br>

PARA VER LAS STATS tiene que ponerle un puerto de escucha asi que vete más abajo pedazo que crack y ponle uno (a tu puto gusto el puerto a elegir).

<br>

Yo lo he puesto en el 25000 y me la pela

<figure><img src=".gitbook/assets/unknown (59).png" alt=""><figcaption></figcaption></figure>

<br>

Por utlimo, que estoy hasta los huevos de esta puta guia mamada, añade una regla en el firewall con el puerto que elegiste en el Frontend.

<br>

Paso de explicarte como hacer la regla que es una paja yo aqui tengo 80 porque puse 80 pero tu pon el que elegiste mama huevazo.

<figure><img src=".gitbook/assets/unknown (60).png" alt=""><figcaption></figcaption></figure>

<br>
