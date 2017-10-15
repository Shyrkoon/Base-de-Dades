# Activitat 2

## Exercici 1

- Canvia el port per defecte de connexió al 3011.

Per canviar el port primer hem de crear un arxiu amb les següents dades iguardar-ho dins de /etc/percona-server.conf.d/mysqld.cnf
[client]
port =  3011


- Quins són els logs activats per defecte? Com ho has fet per comprovar-ho?

Només tenim el log d’errors activat. Ho he pogut veure executant la comanda SHOW GLOBAL VARIABLES LIKE ‘%log’;. També es pot veure al fitxer de configuració de l’anterior apartat.


- Activa si no ho estan i indica les configuracions necessàries per activar-los. Indica les rutes dels fitxer de log de Binary, Slow Query i General. Quins paràmetres has modificat?


Per activar el general log primer he creat una carpeta a /var/log i le he cambiat el propietari de la carpeta.

Despres he afegit la següent informació al fitxer my.cnf.

Per acabar hem de reiniciar el servei de mysql i activar el log a dins del mysql.


A continuació, per activar els logs de slow_queries hem de fer el següent:
Només cal ficar la següent configuració al fitxer my.cnf


Per últim, per els logs binaris, només hem de ficar el següent a dins del fitxer my.cnf:


Per veure el contingut del fitxer hem d'executar la sgüent comanda


## Exercici 2
