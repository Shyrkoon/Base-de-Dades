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


## Exercici 3

- Modifica el fitxer de configuració i desactiva els logs de binary, slow query i genral. Nota: Simplament desactiva'ls no borris altres paràmetres com la ruta dels fitxers, etc...


## Exercici 4
- Activa la els logs en temps d'execució mitjançant la sentència SET GLOBAL. També canvia el destí de log general a una taula (paràmetre log_output). Quines són les sentències que has utilitzat? A quina taula registres els logs general?

## Exercici 5
- Carrega la BD Sakila localitzada a la web de
1.	Descarrega't el fitxer sakila-schema.sql del Moodle.
2.	carrega la BD dins del MySQL utilitzant la sentència:
mysql> SOURCE <ruta_fitxer>/sakila-schema.sql;


## Exercici 6


## Exercici 7


## Exercici 8

