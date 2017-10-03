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

![captura](https://github.com/Shyrkoon/Base-de-dades/blob/master/Activitat1/Imatges/2017-09-19%2019_26_22-ACtividad1%20Percona%20%5BCorriendo%5D%20-%20Oracle%20VM%20VirtualBox.png)

Un cop sabem la contrasenya tenim que accedir a la base de dades utilitzant la següent comanda:

Mysql –h localhost –u root –p

Ara el que tenim que modificar la política de seguretat a LOW
SET validate_password_policy=’LOW’

![captura](https://github.com/Shyrkoon/Base-de-dades/blob/master/Activitat1/Imatges/Captura2.PNG)

Ara tenim que modificar la llargada de la contrasenya, ja que en LOW el mínim és de 8 caracters i la contrasenya proposada en té 6

Llavors el que tenim que fer és el següent:
SET validate_password_length=6

![captura](https://github.com/Shyrkoon/Base-de-dades/blob/master/Activitat1/Imatges/Captura.PNG)

Ara ja podrem canviar a contrasenya del root a patata utilitzat aquesta línia:
ALTER USER 'root'@'localhost' IDENTIFIED BY 'patata'

![captura](https://github.com/Shyrkoon/Base-de-dades/blob/master/Activitat1/Imatges/Captura3.PNG)

## Exercici 2
Per arrancar
  service mysql start

Per reiniciar
  service mysql restart
  
Per detenir
  service mysql stop
 
Per comprovar el status
  service mysql status
  
![captura](https://github.com/Shyrkoon/Base-de-dades/blob/master/Activitat1/Imatges/2017-09-19%2019_07_48-ACtividad1%20Percona%20%5BCorriendo%5D%20-%20Oracle%20VM%20VirtualBox.png)

## Exercici 3

El ftxer de configruació es diu my.cnf i es troba a:

/etc/my.cnf

## Exercici 4

Els fitxers de la base de dades es troben normalment a:

/var/lib/mysql

## Exercici 5

FALTA POR HACER!!!!!!!!!!!!

## Exercici 6

Entrem al arxiu de configuració (my.conf) <br />
Posem el següent: port = port_que_vols_canviar


# Activitat 2 MongoDB

## Instal·lació

Primer de tot, hem entrat a [l'enllaç que ens ha proporcionat el nostre profesor.](https://docs.mongodb.com/master/tutorial/install-mongodb-on-red-hat/)

Ara tenim que seguir el manual. Primer de tot tenim que afegir el repositori de MongoDB a la nostra llista de repositoris. Tenim que accedir al directori on estan els repositoris i crear-ne un per fer aquesta instal·lació

![captura](https://github.com/Shyrkoon/Base-de-dades/blob/master/Activitat1/Imatges/1%20repo.png)

Ara un cop afegit el repositori tenim que fer una instal·lació com qualsevol altre amb la comanda yum, en aquest cas:
yum install mongodb-org

![captura](https://github.com/Shyrkoon/Base-de-dades/blob/master/Activitat1/Imatges/2-1%20install.png)

Seguint el manual hem tingut un problema que és el següent:

![captura](https://github.com/Shyrkoon/Base-de-dades/blob/master/Activitat1/Imatges/3%20semanage.png)

Per resoldre el problema he seguit el següent [MANUAL](https://www.ostechnix.com/linux-troubleshooting-semanage-command-not-found-in-centos-7rhel-7/)

![captura](https://github.com/Shyrkoon/Base-de-dades/blob/master/Activitat1/Imatges/3-1%20semanage.png)

![captura](https://github.com/Shyrkoon/Base-de-dades/blob/master/Activitat1/Imatges/3-2%20ssemanage.png)

Ara si continuem amb la guia d'instal·lació de Mongo ja no ens salta l'error:

![captura](https://github.com/Shyrkoon/Base-de-dades/blob/master/Activitat1/Imatges/4%20semanage.png)

Ara tenim que deshabilitar el SELinux, perque no bloquegi el port que utilitza la base de dades. Reiniciem la maquina perque agafi la configuració, tornem a modificar el mateix arxiu per posar-ho en moded permisiu.

![captura](https://github.com/Shyrkoon/Base-de-dades/blob/master/Activitat1/Imatges/5%20selinux%20disa.png)

![captura](https://github.com/Shyrkoon/Base-de-dades/blob/master/Activitat1/Imatges/6%20selinux%20permi.png)

Finalment ara ja podem arrancar el servei normalment.

un cop que hem iniciat el procès, per accedir solament tenim que escriure en el terminal mongo.

![captura](https://github.com/Shyrkoon/Base-de-dades/blob/master/Activitat1/Imatges/8%20entrar%20al%20mongo.png)

## EXTRA

Ara mateix el servei, el tindrem que iniciar manualment, perque el servei s'iniciï cada vegada que inciem el nostre servidor tindrem que fer el següent

Comprovació de que el dimoni no esta actiu:

![captura](https://github.com/Shyrkoon/Base-de-dades/blob/master/Activitat1/Imatges/9%20extra%20servicio.png)

Activar dimoni

![captura](https://github.com/Shyrkoon/Base-de-dades/blob/master/Activitat1/Imatges/9-1%20extra%20servicio%20automatico.png)






