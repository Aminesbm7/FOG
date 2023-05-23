# Instal·lació i configuració FOG Server

FOG es una eina de programari que pot implementar imatges de disc de Microsoft Windows i Linux utilitzant l'entorn d'execució de pre-arrencada. Fa ús de TFTP, el servidor web Apache i iPXE.


# Sobre quin OS fem la instal·lació?

Realitzarem la instal·lació del FOG server sobre un **Ubuntu 20.04**, ja que estem habituats i perque es mes còmode.

## Instal·lació del servidor FOG

Entrem al lloc web de fog project i descarguem el fitxer tar.gz.
![imatge](/imgs/Selecció_105.png)

Descomprimim el fitxer i entrem a la carpeta /bin i executem el instal·lador
![imatge](/imgs/Selecció_106.png)

![imatge](/imgs/Selecció_107.png)

Dins del instal·lador triem la segona opció "Debian".
![imatge](/imgs/Selecció_108.png)

Triem instal·lacio normal, deixem les interficies per defecte, indiquem la ip del router, si a "handle DHCP" i indiquem la ip del router.
![imatge](/imgs/Selecció_210.png)

Demanara d'accedir al servidor via web per finalitzar la instal·lació.
![imatge](/imgs/Selecció_212.png)

Click sobre "Update/Install now".
![imatge](/imgs/Selecció_213.png)

![imatge](/imgs/Selecció_116.png)

Per acabar la configuració, aturem el servei systemd-resolved i modifiquem l'arxiu "/etc/resolv.conf".
![imatge](/imgs/Selecció_150.png)

Instal·lem "dnsmasq".
![imatge](/imgs/Selecció_151.png)

Creem i configurem "/etc/dnsmasq.d/ltsp.conf" de la següent manera "amb la ip del vostre servidor"
![imatge](/imgs/Selecció_331.png)

## Capturar una imatge Windows

Tenim una imatge **Windows 10 64-bits**, hem instal·lat el chrome ja que no ve per defecte.
![imatge](/imgs/Selecció_264.png)

Entrem al servidor fog via web i creem una nova imatge.
![imatge](/imgs/Selecció_162.png)

A la maquina Windows 10, entrem a configuracio i canviem l'ordre d'arrancada establint com a primera opció la xarxa (tambe es pot realitzar fent clic sobre f12 al boot).

![imatge](/imgs/Selecció_173.png)

Es possible que el IPXE ens demani la ip del servidor FOG.
![imatge](/imgs/Selecció_214.png)

Triem la opcio que es mostra a continuació per afegir el host al servidor FOG.
![imatge](/imgs/Selecció_231.png)

Emplenem els parametres necessaris i triem la imtge que hem creat anteriorment Windows.
![imatge](/imgs/Selecció_266.png)

Ara desde el servidor FOG, a l'apartat "All hosts" apareixera un equip nou.
![imatge](/imgs/Selecció_267.png)

Per identificar-lo li canviem el nom.
![imatge](/imgs/Selecció_268.png)

Finalment per capturar el os, al apartat "All hosts" fem clic sobre la icona taronja "capture" i tornem a iniciar el Windows de la mateixa manera.
![imatge](/imgs/Selecció_269.png)

![imatge](/imgs/Selecció_271.png)

Automaticament es començara a clonar el os.
![imatge](/imgs/Selecció_272.png)

Una vegada finalitzada la tasca podem apagar la maquina.
![imatge](/imgs/Selecció_273.png)

Desde el servidor podem comprovar la mida de la imatge que hem capturat.
![imatge](/imgs/Selecció_274.png)


## Capturar una imatge Ubuntu

Tenim una imatge **Ubuntu 20.04**, hem modificat el tema per defecte per diferenciar-la.
![imatge](/imgs/Selecció_299.png)

Entrem al servidor fog via web i creem una nova imatge per al ubuntu.
![imatge](/imgs/Selecció_276.png)

A la maquina Ubuntu 20.04, entrem a configuracio i canviem l'ordre d'arrancada establint com a primera opció la xarxa (tambe es pot realitzar fent clic sobre f12 al boot).

![imatge](/imgs/Selecció_173.png)

Es possible que el IPXE ens demani la ip del servidor FOG.
![imatge](/imgs/Selecció_214.png)

Triem la opcio que es mostra a continuació per afegir el host al servidor FOG.
![imatge](/imgs/Selecció_231.png)

Emplenem els parametres necessaris, triem la imtge que hem creat anteriorment ubuntu.
![imatge](/imgs/Selecció_252.png)

Ara desde el servidor FOG, a l'apartat "All hosts" apareixera un equip nou.
![imatge](/imgs/Selecció_253.png)

Per identificar-lo li canviem el nom.
![imatge](/imgs/Selecció_254.png)

Finalment per capturar el os, al apartat "All hosts" fem clic sobre la icona taronja "capture" i tornem a iniciar el Ubuntu de la mateixa manera.
![imatge](/imgs/Selecció_255.png)

Automaticament es començara a clonar el os.
![imatge](/imgs/Selecció_257.png)

Una vegada finalitzada la tasca podem apagar la maquina.
Desde el servidor podem comprovar la mida de la imatge que hem capturat.
![imatge](/imgs/Selecció_261.png)

## Desplegar una imatge Windows

Creem una nova maquina virtual amb els parametres necessaris, i li indiquem que arranqui per xarxa com a primera opció.
![imatge](/imgs/Selecció_285.png)

![imatge](/imgs/Selecció_279.png)

El IPXE es probable que ens demani la ip del servidor FOG.
![imatge](/imgs/Selecció_280.png)

Ara al menu triem **"Deploy image"**.
![imatge](/imgs/Selecció_281.png)

Iniciem sessió amb el usuari i contrasenya del servidor FOG.
![imatge](/imgs/Selecció_282.png)

Triem la imatge creada anteriorment per a Windows.
![imatge](/imgs/Selecció_283.png)

Esperem a que es completi la instal·lació de la imatge.
![imatge](/imgs/Selecció_286.png)

Una vegada finalitzada la instal·lació, obrim la maquina i podrem comprovar que conte el chrome instal·lat.
![imatge](/imgs/Selecció_289.png)


## Desplegar una imatge Ubuntu

Creem una nova maquina virtual amb els parametres necessaris, i li indiquem que arranqui per xarxa com a primera opció.
![imatge](/imgs/Selecció_290.png)

![imatge](/imgs/Selecció_291.png)

El IPXE es probable que ens demani la ip del servidor FOG.
![imatge](/imgs/Selecció_292.png)

Ara al menu triem **"Deploy image"**.
![imatge](/imgs/Selecció_293.png)

Iniciem sessió amb el usuari i contrasenya del servidor FOG.
![imatge](/imgs/Selecció_282.png)

Triem la imatge creada anteriorment per a Ubuntu.
![imatge](/imgs/Selecció_295.png)

Esperem a que es completi la instal·lació de la imatge.
![imatge](/imgs/Selecció_297.png)

Una vegada finalitzada la instal·lació, obrim la maquina i podrem comprovar que conte tema modificat.
![imatge](/imgs/Selecció_299.png)


## Snapin packet

Ara que ja tenim les dues imatges desplegades i els hosts al servidor FOG, desplegarem un paquet i que s'instal·li automaticament a un dels clients en aquest cas el Windows 10.

Com a primer pas, obrim el chrome o qualsevol navegador web i accedim a la ip del servidor fog,
alli fem clic sobre **"FOG Client"** situat a la part inferior.
![imatge](/imgs/Selecció_303.png)

Descarreguem el SmartInstaller.

![imatge](/imgs/Selecció_304.png)

Durant la instal·lació, indiquem la ip del servidor fog a l'apartat següent.

![imatge](/imgs/Selecció_307.png)

Una vegada instal·lat el fiquem en marxa a serveis.
![imatge](/imgs/Selecció_309.png)

Seguidament desde el servidor FOG, creem una nova "snapin", com que estem realitzan la instal·lació sobre un equip windows hem triat un fitxer msi de 7zip.
![imatge](/imgs/Selecció_314.png)

Ara a l'apartat "all hosts", entrem al windows i a "snapins" li assignem la que acabem de crear.
![imatge](/imgs/Selecció_315.png)

Per a instal·lar la snapin, entrem a "Basic tasks" del windows 10.
![imatge](/imgs/Selecció_301.png)

A "advanced" triem "Single snapin".
![imatge](/imgs/Selecció_302.png)

Li indiquem la del 7zip i fem clic sobre "Task".
![imatge](/imgs/Selecció_316.png)

Automaticament es crear una tasca per instal·lar el 7zip al client.
![imatge](/imgs/Selecció_311.png)

En molt poc temps ja tindrem el 7zip instal·lat al client, no ens donarem compte de la instal·lació ja que al snapin teniem la opció "/quiet" habilitada.

![imatge](/imgs/Selecció_611.png)
![imatge](/imgs/Selecció_328.png)


Fins aqui el projecte sobre el servidor FOG!

© Amine Sbaay, Guillem Sancho

