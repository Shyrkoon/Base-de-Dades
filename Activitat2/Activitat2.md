# Activitat 2

## Exercici 1

- Canvia el port per defecte de connexió al 3011.

Per canviar el port hem de afegir les següents linies dins de /etc/my.cnf.
[client]
port =  3011

![captura](https://github.com/Shyrkoon/Base-de-dades/blob/master/Activitat2/img/port.png)

- Quins són els logs activats per defecte? Com ho has fet per comprovar-ho?

Només tenim el log d’errors activat. Ho he pogut veure executant la comanda SHOW GLOBAL VARIABLES LIKE ‘%log’;. També es pot veure al fitxer de configuració de /etc/percona-server.conf.d/mysqld.cnf.

![captura](https://github.com/Shyrkoon/Base-de-dades/blob/master/Activitat2/img/foto%20ej%202%201.png)

![captura](https://github.com/Shyrkoon/Base-de-dades/blob/master/Activitat2/img/foto%20ej%202%202.png)

- Activa si no ho estan i indica les configuracions necessàries per activar-los. Indica les rutes dels fitxer de log de Binary, Slow Query i General. Quins paràmetres has modificat?


Per activar el general log primer he creat una carpeta a /var/log i le he cambiat el propietari de la carpeta.

![captura](https://github.com/Shyrkoon/Base-de-dades/blob/master/Activitat2/img/foto%20ej%203%201.png)

Despres he afegit la següent informació al fitxer my.cnf.

![captura](https://github.com/Shyrkoon/Base-de-dades/blob/master/Activitat2/img/foto%20ej%203%202.png)

Per acabar hem de reiniciar el servei de mysql i activar el log a dins del mysql.

![captura](https://github.com/Shyrkoon/Base-de-dades/blob/master/Activitat2/img/foto%20ej%203%205.png)

![captura](https://github.com/Shyrkoon/Base-de-dades/blob/master/Activitat2/img/foto%20ej%203%203.png)


A continuació, per activar els logs de slow_queries hem de fer el següent:
Només cal ficar la següent configuració al fitxer my.cnf

![captura](https://github.com/Shyrkoon/Base-de-dades/blob/master/Activitat2/img/foto%20ej%203%204.png)

![captura](https://github.com/Shyrkoon/Base-de-dades/blob/master/Activitat2/img/foto%20ej%203%206.png)

![captura](https://github.com/Shyrkoon/Base-de-dades/blob/master/Activitat2/img/foto%20ej%203%207.png)

Per últim, per els logs binaris, només hem de ficar el següent a dins del fitxer my.cnf:

![captura](https://github.com/Shyrkoon/Base-de-dades/blob/master/Activitat2/img/foto%20ej%203%208%20V2.png)

Per veure el contingut del fitxer hem d'executar la sgüent comanda

![captura](https://github.com/Shyrkoon/Base-de-dades/blob/master/Activitat2/img/foto%20ej%203%209.png)


## Exercici 2

- Comprova l'estat de les opcions de log que has utilitzat mitjançant una sessió de mysql client.

Aquest es el resultat:

![captura](https://github.com/Shyrkoon/Base-de-dades/blob/master/Activitat2/img/foto%20ej%202%20v1.png)

![captura](https://github.com/Shyrkoon/Base-de-dades/blob/master/Activitat2/img/foto%202%202.png)

## Exercici 3

- Modifica el fitxer de configuració i desactiva els logs de binary, slow query i genral. Nota: Simplament desactiva'ls no borris altres paràmetres com la ruta dels fitxers, etc...

![captura](https://github.com/Shyrkoon/Base-de-dades/blob/master/Activitat2/img/foto%203%201.png)

![captura](https://github.com/Shyrkoon/Base-de-dades/blob/master/Activitat2/img/foto%203%202.png)

## Exercici 4
- Activa la els logs en temps d'execució mitjançant la sentència SET GLOBAL. També canvia el destí de log general a una taula (paràmetre log_output). Quines són les sentències que has utilitzat? 

![captura](https://github.com/Shyrkoon/Base-de-dades/blob/master/Activitat2/img/foto%204%201.png)

![captura](https://github.com/Shyrkoon/Base-de-dades/blob/master/Activitat2/img/foto%204%202.png)

![captura](https://github.com/Shyrkoon/Base-de-dades/blob/master/Activitat2/img/foto%204%203.png)

![captura](https://github.com/Shyrkoon/Base-de-dades/blob/master/Activitat2/img/foto%204%204.png)

![captura](https://github.com/Shyrkoon/Base-de-dades/blob/master/Activitat2/img/foto%204%205.png)

![captura](https://github.com/Shyrkoon/Base-de-dades/blob/master/Activitat2/img/foto%204%206.png)

A quina taula registres els logs general?

![captura](https://github.com/Shyrkoon/Base-de-dades/blob/master/Activitat2/img/foto%204%207.png)

## Exercici 5
- Carrega la BD Sakila localitzada a la web de
1. Descarrega't el fitxer sakila-schema.sql del Moodle.

![captura](https://github.com/Shyrkoon/Base-de-dades/blob/master/Activitat2/img/foto%205%203.png)

2. Carrega la BD dins del MySQL utilitzant la sentència:
mysql> SOURCE <ruta_fitxer>/sakila-schema.sql;

![captura](https://github.com/Shyrkoon/Base-de-dades/blob/master/Activitat2/img/foto%205%202.png)

## Exercici 6
- Compte el numero de sentències CREATE TABLE dins del general log mitjançant:
mysql> SELECT COUNT(*)
	FROM mysql.general_log
	WHERE argument LIKE 'CREATE TABLE%';

![captura](https://github.com/Shyrkoon/Base-de-dades/blob/master/Activitat2/img/foto%206%201.png)

## Exercici 7
- Executa una query mitjançant la funció SLEEP(11) per tal de que es guardi en el log de Slow Query. Mostra el contingut del log demostrant-ho.

![captura](https://github.com/Shyrkoon/Base-de-dades/blob/master/Activitat2/img/foto%207%201.png)

![captura](https://github.com/Shyrkoon/Base-de-dades/blob/master/Activitat2/img/foto%207%202.png)

## Exercici 8
- Assegura't que el Binary Log estigui activat i borra tots els logs anteriors mitjançant la sentència RESET MASTER.

![captura](https://github.com/Shyrkoon/Base-de-dades/blob/master/Activitat2/img/foto%208%201.png)

•	Crea i borra una base de dades anomenada foo. Utilitza la sentències:
		mysql> CREATE DATABASE foo;
		mysql> DROP DATABASE foo;

![captura](https://github.com/Shyrkoon/Base-de-dades/blob/master/Activitat2/img/foto%208%202.png)

•	Mitjançant la sentència SHOW BINLOG EVENTS llista els events i comprova les sentències anteriors en quin fitxer de log estan.

![captura](https://github.com/Shyrkoon/Base-de-dades/blob/master/Activitat2/img/foto%208%203.png)

•	Realitza un Rotate log mitjançant la sentència FLUSH LOGS

![captura](https://github.com/Shyrkoon/Base-de-dades/blob/master/Activitat2/img/foto%208%204.png)

•	Crea i borra una altra base de dades com l'exemple anteior del foo. Però en aquest cas anomena la base de dades bar

![captura](https://github.com/Shyrkoon/Base-de-dades/blob/master/Activitat2/img/foto%208%205.png)

•	Llista tots els fitxers de log i els últims canvis mitjançant la sentència SHOW. Quina sentència has utilitzat? Mostra'n el resultat.

![captura](https://github.com/Shyrkoon/Base-de-dades/blob/master/Activitat2/img/foto%208%206.png)

•	Borra el primer binary log. Quina sentència has utilitzat?

![captura](https://github.com/Shyrkoon/Base-de-dades/blob/master/Activitat2/img/foto%208%207.png)

•	Utilitza el programa mysqlbinlog per mostrar el fitxer mysql-bin.000002
◦	Quin és el seu contingut?

![captura](https://github.com/Shyrkoon/Base-de-dades/blob/master/Activitat2/img/foto%208%208.png)

◦	Quin número d'event ha sigut el de la creació de la base de dades bar?
El 219.
![captura](https://github.com/Shyrkoon/Base-de-dades/blob/master/Activitat2/img/foto%208%209.png)

 ## CONFIGURACIÓ DEL SERVIDOR PERCONA SERVER PER REALITZAR CONNEXIONS SEGURES SOBRE SSL. (3 punts)

Primer de tot tenim que crear les claus, la pública i la privada, per fer-ho he seguit aquesta ![manual](https://dev.mysql.com/doc/refman/5.7/en/creating-ssl-files-using-openssl.html)
El que he fet és crear un script amb les comandes que ens mostra en el manual indicat anteriorment. I l'executem:
![captura](https://github.com/Shyrkoon/Base-de-dades/blob/master/Activitat2/img/3-mysql-certificated.png)



https://dev.mysql.com/doc/refman/5.7/en/using-encrypted-connections.html#using-encrypted-connections-server-side-configuration
