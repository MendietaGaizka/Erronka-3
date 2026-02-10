# VM eta CT Erabilgarritasun handia (HA)

Gaur egun, bi nodoz osatutako Proxmox kluster bat dugu, eta gure enpresak erabilgarritasuna altua (HA) ezartzea saiatu da kudeatzen ditugun makina birtualetan (VM) eta kontainerretan (CT). Ingurune honetan, Windows duen VM bat daukagu, sistema eragile grafikoarekin eta aplikazio espezifikoekin lan egiteko, eta [Ubuntu Server-ean oinarritutako CT bat, Prometheus eta Grafana bidezko monitorizazio zerbitzuak](../) dituztena. HA konfigurazioaren helburua da, nodo bat huts egiten badu, VMak eta CTak automatikoki eskuragarri dagoen nodoan berrabiaraztea, geldialdi-denbora minimizatuz eta enpresako zerbitzu kritikoen jarraikortasuna bermatuz. Erabilgarritasuna altu gaitzeko saiakera egin arren, beharrezkoa da klusterra behar bezala sinkronizatuta dagoela, baliabide partekatuak ondo konfiguratuta daudela eta HA politikak zuzenean ezarriak daudela egiaztatzea, VMak eta CTak funtzionalitate hori modu eraginkorrean aprobetxa dezaten.

<figure><img src="../.gitbook/assets/image (4).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>
