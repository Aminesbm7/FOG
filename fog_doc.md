# Instal·lació i configuració FOG Server

FOG es una eina de programari que pot implementar imatges de disc de Microsoft Windows i Linux utilitzant l'entorn d'execució de pre-arrencada. Fa ús de TFTP, el servidor web Apache i iPXE.


# Sobre quin OS fem la instal·lació?

Realitzarem la instal·lació del FOG server sobre un **Ubuntu 20.04**, ja que estem habituats i perque es mes còmode.

## Instal·lació del servidor FOG

Entrem al lloc web de fog project i descarguem el fitxer tar.gz.
![imatge](/imgs/selecció_105.png)
Descmprimim el fitxer i entrem a la carpeta /bin i executem el instal·lador
imatge
Dins del instal·lador treim la segona opció "Debian".
imatge
Triem instal·lacio normal, deixem les interficies per defecte, indiquem la ip del router, si a "handle DHCP" i indiquem la ip del servidor i a totes les demes opcions per defecte.
imatge
Hens demanara d'accedir al servidor via web per finalitzar la instal·lació.
imatge
Click sobre "Update/Install now".
imatge
Per acabar la configuració, aturem el servei systemd-resolved i modifiquem l'arxiu "/etc/resolv.conf".
imatge
Instal·lem "dnsmasq" i creem i configurem un fitxer de la següent manera "amb la ip del vostre servidor".
imatge

## Capturar una imatge Windows

Tenim una imatge **Windows 10 64-bits**, hem instal·lat el chrome ja que no ve per defecte.
imatge
Entrem al servidor fog via web i creem una nova imatge.
imatge
A la maquina Windows 10, entrem a configuracio i canviem l'ordre d'arrancada establint com a primera opció la xarxa (tambe es pot realitzar fent clic sobre f12 al boot).
imatge
Es possible que el IPXE ens demani la ip del servidor FOG.
imatge
Triem la opcio que es mostra a continuació per afegir el host al servidor FOG.
imatge
Emplenem els parametres necessaris, triem la imtge que hem creat anteriorment Windows.
imatge
Ara desde el servidor FOG, a l'apartat "All hosts" apareixera un equip nou, per identificar-lo li canviem el nom.
imatge
Finalment per capturar el os, al apartat "All hosts" fem clic sobre la icona taronja "capture" i tornem a iniciar el Windows de la mateixa manera.
imatge
Automaticament es començara a clonar el os.
imatge
Una vegada finalitzada la tasca podem apagar la maquina.
imatge
Desde el servidor podem comprovar la mida de la imatge que hem capturat.
imatge
## Capturar una imatge Ubuntu

Tenim una imatge **Ubuntu 20.04**, hem modificat el tema per defecte per diferenciar-la.
imatge
Entrem al servidor fog via web i creem una nova imatge per al ubuntu.
imatge
A la maquina Ubuntu 20.04, entrem a configuracio i canviem l'ordre d'arrancada establint com a primera opció la xarxa (tambe es pot realitzar fent clic sobre f12 al boot).
imatge
Es possible que el IPXE ens demani la ip del servidor FOG.
imatge
Triem la opcio que es mostra a continuació per afegir el host al servidor FOG.
imatge
Emplenem els parametres necessaris, triem la imtge que hem creat anteriorment ubuntu.
imatge
Ara desde el servidor FOG, a l'apartat "All hosts" apareixera un equip nou, per identificar-lo li canviem el nom.
imatge
Finalment per capturar el os, al apartat "All hosts" fem clic sobre la icona taronja "capture" i tornem a iniciar el Ubuntu de la mateixa manera.
imatge
Automaticament es començara a clonar el os.
imatge
Una vegada finalitzada la tasca podem apagar la maquina.
imatge
Desde el servidor podem comprovar la mida de la imatge que hem capturat.
imatge

## Desplegar una imatge Windows

Creem una nova maquina virtual amb els parametres necessaris, i li indiquem que arranqui per xarxa com a primera opció.
imatge
El IPXE es probable que ens demani la ip del servidor FOG.
imatge
Ara al menu triem **"Deploy image"**.
imatge
Iniciem sessió amb el usuari i contrasenya del servidor FOG.
imatge
Triem la imatge creada anteriorment per a Windows.
imatge
Esperem a que es completi la instal·lació de la imatge.
imatge
Una vegada finalitzada la instal·lació, obrim la maquina i podrem comprovar que conte el chrome instal·lat.
imatge


## Desplegar una imatge Ubuntu

Creem una nova maquina virtual amb els parametres necessaris, i li indiquem que arranqui per xarxa com a primera opció.
imatge
El IPXE es probable que ens demani la ip del servidor FOG.
imatge
Ara al menu triem **"Deploy image"**.
imatge
Iniciem sessió amb el usuari i contrasenya del servidor FOG.
imatge
Triem la imatge creada anteriorment per a Ubuntu.
imatge
Esperem a que es completi la instal·lació de la imatge.
imatge
Una vegada finalitzada la instal·lació, obrim la maquina i podrem comprovar que conte tema modificat.
imatge


## Snapin packet

Ara que ja tenim les dues imatges desplegades i els hosts al servidor FOG, desplegarem un paquet i que s'instal·li automaticament a un dels clients en aquest cas el Windows 10.

Com a primer pas, obrim el chrome o qualsevol navegador web i accedim a la ip del servidor fog,
alli fem clic sobre **"FOG Client"** situat a la part inferior.
imatge
Descarreguem el SmartInstaller.
imatge
Durant la instal·lació, indiquem la ip del servidor fog a l'apartat següent.
imatge
Una vegada instal·lat el fiquem en marxa a serveis.
imatge
Seguidament desde el servidor FOG, creem una nova "snapin", com que estem realitzan la instal·lació sobre un equip windows hem triat un fitxer msi de 7zip.
imatge
Ara a l'apartat "all hosts", entrem al windows i a "snapins" li assignem la que acabem de crear.
imatge
Per a instal·lar la snapin, entrem a "Basic tasks" del windows 10 i "advanced" triem "Single snapin" i li indiquem la del 7zip i fem clic sobre "Task".
imatge
Automaticament es crear una tasca per instal·lar el 7zip al client.
imatge
En molt poc temps ja tindrem el 7zip instal·lat al client, no ens domarem compte de la instal·lació ja que al snapin teniem la opció "/quiet" habilitada.
imatge


Hasta aqui el projecte sobre el servidor FOG!

```mermaid
Authors 
Amine Sbaay -- Guillem Sancho
```

