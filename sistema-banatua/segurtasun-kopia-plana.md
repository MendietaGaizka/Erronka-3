# Segurtasun kopia plana

Sistema Banatuak irakasgaian, segurtasun kopien plan bat ezarri da, bi nodok osatutako Proxmox kluster batean exekutatzen diren zerbitzu birtualizatuak babesteko. Plan honen helburua da sistemaren akatsen, konfigurazio-akatsen edo datu-galeren aurrean makina birtualen eta edukiontzien erabilgarritasuna eta berreskurapena bermatzea, ingurune banatuetako berezko kontzeptuak aplikatuz.

Ingurunea bi nodo dituen Proxmox VE kluster batek eta Proxmox Backup Server zerbitzari batek osatzen dute, eta segurtasun kopiak egiteko eta biltegiratzeko soilik erabiltzen da. Klusterraren barruan makina birtual bat eta edukiontzi bat zabaltzen dira, eta horiek planaren irismenaren parte dira. Benetako eskuragarritasun handiak gutxienez hiru nodo eskatzen baditu ere, kasu honetan kontzeptua modu akademikoan eta funtzionalean lantzen da.

Babeskopiak Proxmox Backup Server bidez egiten dira. Horri esker, bloke mailan backup inkrementalak egin daitezke, biltegiratzearen erabilera optimizatuz datuen deduplikazioari eta konpresioari esker. Kopia zerbitzaria zuzenean integratzen da Proxmox VErekin, eta horrek prozesu osoa klusterraren administrazio-interfazetik bertatik kudeatzeko aukera ematen du.

Sistema makina birtualaren eta edukiontziaren hasierako kopia osoa egiteko konfiguratzen da, eta, ondoren, automatikoki programatutako kopia inkrementalak egiteko. Kopia horiek karga txikiko ordutegietan exekutatzen dira, klusterraren errendimenduan ahalik eta eragin txikiena izateko. Gainera, sistema bakoitzaren bertsio historiko bat baino gehiago gordetzea ahalbidetzen duen atxikipen-politika bat ezartzen da, duela gutxiko akatsen edo ondoren antzemandako arazoen aurrean berreskuratzea erraztuz.

Nodoetako batek huts egiten badu, planak aurreikusten du makina birtuala edo edukiontzia lehengoratzea klusterraren gainerako nodoan, Proxmox Backup Server-en biltegiratutako kopietatik abiatuta. Horrela, erabilgarritasun handiko agertoki bat simulatzen da, zerbitzuaren berreskuratze eta jarraitutasun ahalmena erakutsiz, ingurunea bi nodotara mugatuta egon arren.

Planaren funtzionamendu egokia egiaztatzeko, makina birtualaren eta edukiontziaren proba-berrezarpenak egiten dira, sistemak behar bezala abiatzen direla eta zerbitzuek modu egokian funtzionatzen dutela egiaztatuz. Prozesu horrek kopien fidagarritasuna baliozkotzea ahalbidetzen du, eta sistema azkar eta eraginkortasunez berreskura daitekeela bermatzen du.

Oro har, babeskopien plan honek irtenbide sendoa eta profesionala eskaintzen du sistema banatuen ingurune baterako, enpresa azpiegituretan erabilitako eta testuinguru akademiko batera egokitutako jardunbide egokiak aplikatuz.

<br>
