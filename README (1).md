# adrekin konexioa , rol , check session

## AD REKIN KONEXIOA:

konfigurazioa:\
\<?php

$db\_host="localhost";

$db\_user="root";

$db\_pass="Admin123";

$db\_name="2erronkabn";

$ad\_server="ldap://192.168.0.1";

$ad\_domain="punkets.lan";

$ad\_base\_dn="OU=banco\_punkets,DC=punkets,DC=lan";

<br>

<br>

en login.php:\
<br>

/\* ===== CONEXIÓN A AD ===== \*/

$ldap = ldap\_connect($ad\_server);

if (!$ldap) {

&#x20;   echo json\_encode(\["success" => false]);

&#x20;   exit;

}

<br>

ldap\_set\_option($ldap, LDAP\_OPT\_PROTOCOL\_VERSION, 3);

ldap\_set\_option($ldap, LDAP\_OPT\_REFERRALS, 0);

<br>

/\* ===== BIND ===== \*/

if (!@ldap\_bind($ldap, "$user@$ad\_domain", $pass)) {

&#x20;   echo json\_encode(\["success" => false]);

&#x20;   exit;

}

\
\
\
\
\
\
\
<br>

## rol Admin no admin

logeatzen denean admin bat&#x20;

<figure><img src=".gitbook/assets/unknown (6) (1) (1).png" alt=""><figcaption></figcaption></figure>

<br>

ez admin bat logeatzean:&#x20;

<figure><img src=".gitbook/assets/unknown (7) (1) (1).png" alt=""><figcaption></figcaption></figure>

<br>

rolak jsan:\
&#x20; if (data.role === "admin") {

&#x20;               if (!location.pathname.endsWith("home.html")) {

&#x20;                   location.href = "home.html";

&#x20;               }

&#x20;           } else {

&#x20;               if (!location.pathname.endsWith("orrinagusia\_user.html")) {

&#x20;                   location.href = "orrinagusia\_user.html";

&#x20;               }

&#x20;           }

\
\
\
<br>

## CHECKSESION:

rolak ere ikusteko editatu dugu:\
checsesion.php:\
\<?php

session\_start();

<br>

header("Content-Type: application/json");

<br>

if (isset($\_SESSION\["user"]) && isset($\_SESSION\["role"])) {

&#x20;   echo json\_encode(\[

&#x20;       "logged" => true,

&#x20;       "user" => $\_SESSION\["user"],

&#x20;       "role" => $\_SESSION\["role"]

&#x20;   ]);

} else {

&#x20;   echo json\_encode(\[

&#x20;       "logged" => false

&#x20;   ]);

}

<br>

\
<br>

js an

<br>

function checkSession() {

&#x20;   fetch("php/auth/checkSession.php")

&#x20;       .then(response => response.json())

&#x20;       .then(data => {

<br>

&#x20;           // No logueado

&#x20;           if (!data.logged) {

&#x20;               if (!location.pathname.endsWith("index.html")) {

&#x20;                   location.href = "index.html";

&#x20;               } else {

&#x20;                   loadLogin();

&#x20;               }

&#x20;               return;

&#x20;           }

<br>

&#x20;           // Logueado → redirigir por rol

&#x20;           if (data.role === "admin") {

&#x20;               if (!location.pathname.endsWith("home.html")) {

&#x20;                   location.href = "home.html";

&#x20;               }

&#x20;           } else {

&#x20;               if (!location.pathname.endsWith("orrinagusia\_user.html")) {

&#x20;                   location.href = "orrinagusia\_user.html";

&#x20;               }

&#x20;           }

<br>

&#x20;           // Mostrar usuario si existe

&#x20;           if (typeof user !== "undefined") {

&#x20;               user.innerText = data.user;

&#x20;           }

<br>

&#x20;           // Botón logout si existe

&#x20;           if (typeof btnLogout !== "undefined") {

&#x20;               btnLogout.onclick = logout;

&#x20;           }

&#x20;       });

}

\
\
\
\
\
\
\
\
\
\
\
\
\
\
\
\
\
\
<br>
