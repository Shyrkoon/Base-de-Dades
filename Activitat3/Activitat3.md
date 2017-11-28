# Activitat 1. REALITZA I/O RESPON ELS SEGÜENTS APARTATS (1 punts)

## 1. Indica quins són els motors d’emmagatzematge que pots utilitzar (quins estan actius)? Mostra al comanda utilitzada i el resultat d’aquesta.

Es pot veure utiltizant la comanda SHOW ENGINES\G;

![captura](https://github.com/Shyrkoon/Base-de-dades/blob/master/Activitat3/img/foto%20ac1%201.PNG)

![captura](https://github.com/Shyrkoon/Base-de-dades/blob/master/Activitat3/img/foto%20ac1%202.PNG)


## 2. Com puc saber quin és el motor d’emmagatzematge per defecte. Mostra com canviar aquest paràmetre de tal manera que les noves taules que creem a la BD per defecte utilitzin el motor MyISAM?

Es pot fer de 3 maneres diferents:
- Una es especificant el motor que volem al crear una taula. Per exemple: CREATE TABLE t1 (i INT) ENGINE = INNODB;
- La segona es mitjançant la variable de sessió d'usuari: @@storage_engine
- Una altra es modificant el fitxer de configuració my.cnf afegint el següent: default-storage-engine=InnoDB
- També es pot especificar només per a la sessió en la que estem: SET defaul_storage_engine=InnoDB

## 3. Com podem saber quin és el motor d'emmagatzematge per defecte?
Es pot veure amb l'anterior comanda: SHOW ENGINES\G;
Hem de buscar quin es el sistema que té un parametre: DEFAULT.

![captura](https://github.com/Shyrkoon/Base-de-dades/blob/master/Activitat3/img/foto%20ac1%203.PNG)


## 4. Explica els passos per instal·lar i activar l'ENGINE MyRocks. MyRocks és un motor d'emmagatzematge per MySQL basat en RocksDB (SGBD incrustat de tipus clau-valor).
Hem seguit aquesta guia: https://www.percona.com/doc/percona-server/LATEST/myrocks/install.html#installing-percona-myrocks



![captura](https://github.com/Shyrkoon/Base-de-dades/blob/master/Activitat3/img/rocks1.png)
![captura](https://github.com/Shyrkoon/Base-de-dades/blob/master/Activitat3/img/rocks2.png)
![captura](https://github.com/Shyrkoon/Base-de-dades/blob/master/Activitat3/img/rock%20install.png)
![captura](https://github.com/Shyrkoon/Base-de-dades/blob/master/Activitat3/img/db_create.png)
![captura](https://github.com/Shyrkoon/Base-de-dades/blob/master/Activitat3/img/activate_db.png)

![captura](https://github.com/Shyrkoon/Base-de-dades/blob/master/Activitat3/img/Creating_db_rockdb.png)

Checkpoint: Mostra al professor que està instal·lat i posa un exemple de com funciona.
## 5. Importa la BD Sakila com a taules MyISAM. Fes els canvis necessaris per importar la BD Sakila perquè totes les taules siguin de tipus MyISAM. 
Mira quins són els fitxers físics que ha creat, quan ocupen i quines són les seves extensions. Mostra'n una captura de pantalla i indica què conté cada fitxer.

Nosaltres ho hem fet subtituint tots els ENGINE=InnoDB que hi ha al codi de sakila-schema.
Primer ens hem de baixar el codi.

![captura](https://github.com/Shyrkoon/Base-de-dades/blob/master/Activitat3/img/foto%20ac1%205%201.PNG)

Un cop que el tenim, podem utilitzar qualsevol editor de textos que tingui una eina de "Buscar y Substituir".

![captura](https://github.com/Shyrkoon/Base-de-dades/blob/master/Activitat3/img/foto%20ac1%205%203.PNG)

![captura](https://github.com/Shyrkoon/Base-de-dades/blob/master/Activitat3/img/foto%20ac1%205%204.PNG)

Ho guardem i importem la base de dades al CentOS.

![captura](https://github.com/Shyrkoon/Base-de-dades/blob/master/Activitat3/img/foto%20ac1%205%205.PNG)

Per últim utilitzem la comanda: SOURCE (ruta)/sakila-schema.sql desde el nostre mysql per importar la base de dades de sakila.

![captura](https://github.com/Shyrkoon/Base-de-dades/blob/master/Activitat3/img/foto%20ac1%205%206.PNG)

Amb la comanda SHOW TABLE STATUS FROM sakila; podem veure que les taules s'han creat amb MyISAM.

![captura](https://github.com/Shyrkoon/Base-de-dades/blob/master/Activitat3/img/foto%20ac1%205%207.PNG)

Per cada taula es creen 3 fitxers diferens:
- .MYI: En aquest fitxer és guarden els fitxers d'índex.
- .MYD: Aquí es on es guarden les dades de la taula.
- .frm: És on es guarda el format de la taula.

![captura](https://github.com/Shyrkoon/Base-de-dades/blob/master/Activitat3/img/foto%20ac1%205%208.PNG)

Aquí podem veure el que ocupa cada un dels fitxers. El de les dades està buit ja que no tenim dades a cap taula.

![captura](https://github.com/Shyrkoon/Base-de-dades/blob/master/Activitat3/img/foto%20ac1%205%209.PNG)


# Activitat 2. INNODB part I. REALITZA ELS SEGÜENTS APARTATS. (2 punts)

## 1. Importa la BD Sakila com a taules InnoDB. 

![captura](https://github.com/Shyrkoon/Base-de-dades/blob/master/Activitat3/img/2.1.png)


## 2. Quin/quins són els fitxers de dades? A on es troben i quin és la seva mida?

Per defecte mysql guarda els fitxers a: /var/lib/mysql/(nom de la base de dades).
Si entrem a la carpeta de la base de dades de sakila podem veure tots els fitxers que té:

![captura](https://github.com/Shyrkoon/Base-de-dades/blob/master/Activitat3/img/foto%20ac2%202%201.PNG)

Podem veure que cada taula té un fitxer per a les dades i un per al format de la taula.

Aqui podem veure que el ocupa cada fitxer:

![captura](https://github.com/Shyrkoon/Base-de-dades/blob/master/Activitat3/img/foto%20ac2%202%202.PNG)

També estan el fitxers d'índex i cache, tots ells amb una mida predefinida.

![captura](https://github.com/Shyrkoon/Base-de-dades/blob/master/Activitat3/img/foto%20ac2%202%203.PNG)


## 3. Canvia la configuració del MySQL perqurè:
- Canviar la localització dels fitxers del tablespace de sistema per defecte a /discs-mysql/
- Tinguem dos fitxers corresponents al tablespace de sistema.
- Tots dos han de tenir la mateixa mida inicial (1MB) 
- El tablespace ha de creixer de 1MB en 1MB.
- Situa aquests fitxers (de manera relativa a la localització per defecte) en una nova localització simulant el següent:
 /discs-mysql/disk1/primer fitxer de dades → simularà un disc dur
 /discs-mysql/disk2/segon fitxer de dades → simularà un segon disc dur.
 

Primer hem d'escriure la següent configuració al fitxer de configuració del mysql.

![captura](https://github.com/Shyrkoon/Base-de-dades/blob/master/Activitat3/img/foto%20ac2%203%201.PNG)

Un cop guardat creem les carpetes on guardarem els nous arxius.

Probablement ens donarà un error quan iniciem el servei. Si miren als fitxers .log del mysql ens dirà que hem de borrar el fitxers logfile del mysql.

![captura](https://github.com/Shyrkoon/Base-de-dades/blob/master/Activitat3/img/foto%20ac2%203%203.PNG)

Ara reiniciem el servei per tal de que tots els canvin tinguin efecte.
 
![captura](https://github.com/Shyrkoon/Base-de-dades/blob/master/Activitat3/img/foto%20ac2%203%202.PNG)

Si ens dona problemes, podem probar a desactivar el selinux.

![captura](https://github.com/Shyrkoon/Base-de-dades/blob/master/Activitat3/img/foto%20ac2%203%204.PNG)

Per acabar comprovem que s'han creat automàticament 2 fitxers, un a cada carpeta.

![captura](https://github.com/Shyrkoon/Base-de-dades/blob/master/Activitat3/img/foto%20ac2%203%205.PNG)


## 4. Checkpoint: Mostra al professor els canvis realitzats i que la BD continua funcionant.


# Activitat 3. INNODB part II. REALITZA ELS SEGÜENTS APARTATS. (1 punt)

## 1. Partint de l'esquema anterior configura el Percona Server perquè cada taula generi el seu propi tablespace en una carpeta anomenada tspaces (aquesta pot estar situada a on vulgueu). 
## 1. Indica quins són els canvis de configuració que has realitzat.

Primer hem de modificar la següent configuració:

![captura](https://github.com/Shyrkoon/Base-de-dades/blob/master/Activitat3/img/foto%20ac3%202.PNG)

Ara podem fer la seguent comanda a dins del Mysql per activar el file per table o reiniciar el servei.

![captura](https://github.com/Shyrkoon/Base-de-dades/blob/master/Activitat3/img/foto%20ac3%201.PNG)

Ara que ja està activat podem probar com funciona. 
Amb el següent script he passat una base de dades de MyISAM a innodb per probar el funcionament.

![captura](https://github.com/Shyrkoon/Base-de-dades/blob/master/Activitat3/img/foto%20ac3%203.PNG)

![captura](https://github.com/Shyrkoon/Base-de-dades/blob/master/Activitat3/img/foto%20ac3%204.PNG)

A les següents taules que afegim a la base de dades o les que modifiquem tindrien que estar cada una en una carpeta amb el nom que tenen.

## 2. Després del canvi què ha passat amb els fitxers que contenien les dades de la BD de Sakila? Fes les captures necesàries per complementar la resposta.

![captura](https://github.com/Shyrkoon/Base-de-dades/blob/master/Activitat3/img/foto%20ac3%205.PNG)


# Activitat 4. INNODB part III. REALITZA ELS SEGÜENTS APARTATS. (1 punts)

## 1. Crea un tablespace anomenat 'ts1' situat a /discs-mysql/disc1/ i col·loca les taules actor, address i category de la BD Sakila.
## 2. Crea un altre tablespace anomenat 'ts2' situat a /discs-mysql/disc2/ i col·loca-hi la resta de taules.

![captura](https://github.com/Shyrkoon/Base-de-dades/blob/master/Activitat3/img/img%20ac4%201.PNG)

## 3. Comprova que pots realitzar operacions DML a les taules dels dos tablespaces.

A continuació es mostra com canvio el tablespace d'una taula e insereixo molts registres per veure si canvia la mida de ts1.ibd:

![captura](https://github.com/Shyrkoon/Base-de-dades/blob/master/Activitat3/img/img%20ac4%205.PNG)

![captura](https://github.com/Shyrkoon/Base-de-dades/blob/master/Activitat3/img/img%20ac4%209.PNG)

![captura](https://github.com/Shyrkoon/Base-de-dades/blob/master/Activitat3/img/img%20ac4%2010.PNG)

![captura](https://github.com/Shyrkoon/Base-de-dades/blob/master/Activitat3/img/img%20ac4%2011.PNG)


## 4. Quines comandes i configuracions has realitzat per fer els dos apartats anteriors?

Primer he creat les dues carpetes.

![captura](https://github.com/Shyrkoon/Base-de-dades/blob/master/Activitat3/img/img%20ac4%201.PNG)

A continuació he canviat els permisos de les carpetes que he creat ja que pot donar problemes a l'hora de crear els tablespaces.

![captura](https://github.com/Shyrkoon/Base-de-dades/blob/master/Activitat3/img/img%20ac4%203.PNG)

![captura](https://github.com/Shyrkoon/Base-de-dades/blob/master/Activitat3/img/img%20ac4%202.PNG)

Ara hem de crear els tablespaces.

![captura](https://github.com/Shyrkoon/Base-de-dades/blob/master/Activitat3/img/img%20ac4%204.PNG)

Per últim hem de canviar el tablespace de cada taula per el nou que acabem de crear.

![captura](https://github.com/Shyrkoon/Base-de-dades/blob/master/Activitat3/img/img%20ac4%205.PNG)

![captura](https://github.com/Shyrkoon/Base-de-dades/blob/master/Activitat3/img/img%20ac4%206.PNG)

![captura](https://github.com/Shyrkoon/Base-de-dades/blob/master/Activitat3/img/img%20ac4%207.PNG)

![captura](https://github.com/Shyrkoon/Base-de-dades/blob/master/Activitat3/img/img%20ac4%208.PNG)


## 5. Checkpoint: Mostra al professor els canvis realitzats i que la BD continua funcionant





# Activitat 5. REDOLOG. REALITZA ELS SEGÜENTS APARTATS. (2 punt)

## 1. Com podem comprovar (Innodb Log Checkpointing):
LSN (Log Sequence Number)
L'últim LSN actualitzat a disc
Quin és l'últim LSN que se li ha fet Checkpoint

Tot això ho podrem trobar executant la comanda:

"SHOW ENGINE INNODB STATUS\G"
I tenim que anar a buscar l'apartat de LOG

![captura](https://github.com/Shyrkoon/Base-de-dades/blob/master/Activitat3/img/bd-5-1.png)

El LSN en el nostre cas és el 2786026
L'última que ha actualitzat a disc 2786026
I l'ultima checkpoint que ha fer és el 2786017

## 3. Com podem mirar el número de pàgines modificades (dirty pages)? I el número total de pàgines?

Utilitzem la mateixa comanda "SHOW ENGINE INNODB STATUS\G".
En aquest cas tenim que buscar l'apartat de BUFFER POOL AND MEMORY

![captura](https://github.com/Shyrkoon/Base-de-dades/blob/master/Activitat3/img/bd-5-2.png)

El numero total de pàgines es el Database pages 405
Modified db pages són les pàgines pendents, en el meu cas no en tinc cap pendent.


## 4. Checkpoint: Mostra al professor els canvis realitzats i que la BD continua funcionant.
# Activitat 6. Implentar BD Distribuïdes. (2 punt)

Com s'ha vist a classe MySQL proporciona el motor d'emmagatzemament FEDERATED que té com a funció permetre l'accés remot a bases de dades MySQL en un servidor local sense utilitzar tècniques de replicació ni clustering.


## 1. Prepara un Servidor Percona Server amb la BD de Sakila
## 2. Prepara un segon servidor Percona Server a on hi hauran un conjunt de taules FEDERADES al primer servdor.
## 3. Per realitzar aquest link entre les dues BD podem fer-ho de dues maneres:
#### 1. Opció1: especificar TOTA la cadena de connexió a CONNECTION 
#### 2. Opció2: especifficar una connexió a un server a CONNECTION que prèviament s'ha creat mitjançant CREATE SERVER
## 3. Posa un exemple de 2 taules de cada opció. 
Tingues en compte els permisos a nivell de BD i de SO així com temes de seguretat com firewalls, etc...
## 4. Detalla quines són els passos i comandes que has hagut de realitzar en cada màquina.
## 4. Checkpoint: Mostra al professor la configuració que has hagut de realitzar i el seu funcionament.

# Activitat 7. Storage Engine CSV (1 punt)
## 1. Documenta i posa exemple de com utilitzar ENGINE CSV.
## 2. Cal documentar els passos que has hagut de realitzar per preparar l'exemple: configuracions, instruccions DML, DDL, etc....

Primer de tot tenim que mirar si està actiu l'ENGINE del CSV en el nostre MySql, podem fer-ho utilitzant:
![captura](https://github.com/Shyrkoon/Base-de-dades/blob/master/Activitat3/img/bdex64.png)

Ara el que tenim que fer és crear la BD dins del nostre SQL, nosaltres hem creat la BD csv.
Ara un cop creat el que tenim que fer és crear la taula. Important de que els camps siguin "Not Null".

![captura](https://github.com/Shyrkoon/Base-de-dades/blob/master/Activitat3/img/bdex61.png)
![captura](https://github.com/Shyrkoon/Base-de-dades/blob/master/Activitat3/img/bdex62.png)

Ara el que fem és introduir dades, i aquestes dades ho podrem veure en l'arxiu de la base de dades en format CSV.
![captura](https://github.com/Shyrkoon/Base-de-dades/blob/master/Activitat3/img/bdex63.png)

A part el que haviem fet era importar desde un arxiu CSV algunes dades.
![captura](https://github.com/Shyrkoon/Base-de-dades/blob/master/Activitat3/img/bdex65.png)


## 3. Checkpoint: Mostra al professor la configuració que has hagut de realitzar i el seu funcionament.





