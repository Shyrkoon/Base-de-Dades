# Activitat 1

## Instal·lació
Per començar hem d'agafar el paquet amb la següent comanda:
(sudo) wget https://www.percona.com/downloads/Percona-Server-5.7/Percona-Server-5.7.10-3/binary/redhat/7/x86_64/Percona-Server-5.7.10-3-r63dafaf-el7-x86_64-bundle.tar

Per descomprimir el paquet fem: tar xvf Percona-Server-5.7.10-3-r63dafaf-el7-x86_64-bundle.tar

Per instal·lar 
rpm -ivh Percona-Server-server-57-5.7.10-3.1.el7.x86_64.rpm \
Percona-Server-client-57-5.7.10-3.1.el7.x86_64.rpm \
Percona-Server-shared-57-5.7.10-3.1.el7.x86_64.rpm

## Exercici 1

Per poder trobar la password del root tenim que fer un cat del fitxer log del mysql de percona y buscar exactament : temporary password

![captura](/Imatges/Captura3.png)

Un cop sabem la contrasenya tenim que accedir a la base de dades utilitzant la següent comanda:

Mysql –h localhost –u root –p

Ara el que tenim que modificar la política de seguretat a LOW
SET validate_password_policy=’LOW’
Ara tenim que modificar la llargada de la contrasenya, ja que en LOW el mínim és de 8 caracters i la contrasenya proposada en té 6

Llavors el que tenim que fer és el següent:
SET validate_password_length=6

Ara ja podrem canviar a contrasenya del root a patata utilitzat aquesta línia:
ALTER USER 'root'@'localhost' IDENTIFIED BY 'patata'


## Exercici 2
Per arrancar
  service mysql start

Per reiniciar
  service mysql restart
  
Per detenir
  service mysql stop
 
Per comprovar el status
  service mysql status

## Exercici 3

/etc/mysql/my.cnf

## Exercici 4


## Exercici 5

SET GLOBAL validate_password_policy=LOW;

SET GLOBAL validate_password_length=6;

SET PASSWORD = PASSWORD('patata');

## Exercici 6

Entrem al arxiu de configuració (my.conf) <br />
Posem el següent: port = port_que_vols_canviar
## Exercici 7

# Activitat 2 MYSQL

## Instal·lació

## Exercici 1
## Exercici 2
## Exercici 3
## Exercici 4
## Exercici 5
## Exercici 6
## Exercici 7
## Exercici 8
## Exercici 9
## Exercici 10
