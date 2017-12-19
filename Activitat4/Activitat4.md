# REPLICACIÓ via Binlog
## Master

Per començar hem d'entrar al fixer de configuració del mysql i activar els log binaris. Abans de fer qualsevol canvi es recomanable fer una copia de seguretat d'aquest fitxer. També hem d'afegir la línia server-id i un número per identificar el servidor. Al Slave també haurem de ficar el mateix (només el server-id) però amb un número diferent.

![Captura](https://github.com/Shyrkoon/Base-de-dades/blob/master/Activitat4/img/cap1.png)

Ara hem d'apagar el servei i borrar tots els fitxers de log que té creats la base de dades dintre de /var/lib/mysql. Un cop que els tenim borrats, tornem a encendre el servei i podrem veure que ha creat de nous amb el nom que hem indicat abans.

![Captura](https://github.com/Shyrkoon/Base-de-dades/blob/master/Activitat4/img/cap2.png)

Ara mirem el contingut dels logs binaris que s'han creat. És recomanable mirar sempre l'últim que s'ha creat. Hem de buscar la línia que fica "end_log_pos". En aquest cas (en la segona captura) ens indica que és el número 154.

![Captura](https://github.com/Shyrkoon/Base-de-dades/blob/master/Activitat4/img/cap3%20cat%20rep%20archivo.png)

![Captura](https://github.com/Shyrkoon/Base-de-dades/blob/master/Activitat4/img/cap4%20cat%20rep%20archivo.png)

Ara hem de crear un usuari que servirà per fer les replicacions. Aquest usuari tindrà de nom slave i la ip de la màquina slave. També hem de donar permisos de replicació a aquest usuari.

![Captura](https://github.com/Shyrkoon/Base-de-dades/blob/master/Activitat4/img/cap5%20usuari.png)

Per últim executem la comanda flush logs i comprovem que estan activats i creats correctament.

![Captura](https://github.com/Shyrkoon/Base-de-dades/blob/master/Activitat4/img/cap8.png)




## Slave

A continuació configurarem l'slave.
Primer hem d'assignar un server id diferent de la màquina master.

![Captura](https://github.com/Shyrkoon/Base-de-dades/blob/master/Activitat4/img/cap6%20slave.png)

Com que les màquines han de tenir la mateixa informació per començar amb la replica, importem les bases de dades que té la màquina master.

![captura](https://github.com/Shyrkoon/Base-de-dades/blob/master/Activitat4/img/cap9.png)

Ara hem d'executar les següents comandes, les quals tenen informació de la màquina master.

![Captura](https://github.com/Shyrkoon/Base-de-dades/blob/master/Activitat4/img/cap10.png)

I executar la comanda start slave:

![Captura](https://github.com/Shyrkoon/Base-de-dades/blob/master/Activitat4/img/cap12.png)

Per comprovar si la màquina slave està ben configurada i està replicant del master ho podem comprovar amb la comanda show slave status \G;

![captura](https://github.com/Shyrkoon/Base-de-dades/blob/master/Activitat4/img/cap13.png)

Ara comprovarem si la replica funciona creant unes taules en el servidor master.

![captura](https://github.com/Shyrkoon/Base-de-dades/blob/master/Activitat4/img/cap14.png)

Creem una taula, comprovem que esta en el servidor slave i creem una segona taula en el master i instantaneament comprovem que també s'ha creat en el servidor slave.

![captura](https://github.com/Shyrkoon/Base-de-dades/blob/master/Activitat4/img/cap15.png)


