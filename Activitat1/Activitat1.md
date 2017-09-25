# Activitat 1

## Exercici 1
Per començar hem d'agafar el paquet amb la següent comanda:
(sudo) wget https://www.percona.com/downloads/Percona-Server-5.7/Percona-Server-5.7.10-3/binary/redhat/7/x86_64/Percona-Server-5.7.10-3-r63dafaf-el7-x86_64-bundle.tar

Per descomprimir el paquet fem: tar xvf Percona-Server-5.7.10-3-r63dafaf-el7-x86_64-bundle.tar

Per instal·lar 
rpm -ivh Percona-Server-server-57-5.7.10-3.1.el7.x86_64.rpm \
Percona-Server-client-57-5.7.10-3.1.el7.x86_64.rpm \
Percona-Server-shared-57-5.7.10-3.1.el7.x86_64.rpm

## Exercici 2

## Exercici 3

Per arrancar
  service mysql start

Per reiniciar
  service mysql restart
  
Per detenir
  service mysql stop
 
Per comprovar el status
  service mysql status
