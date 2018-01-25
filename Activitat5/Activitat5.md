# Clustering XtraDB

## Configuració Percona Cluster

Primer de tot tenim que afegir el repositori en la nostre llista de repositoris. Per això utilitzem:

![Captura](https://github.com/Shyrkoon/Base-de-dades/blob/master/Activitat5/img/c1.png)

![Captura](https://github.com/Shyrkoon/Base-de-dades/blob/master/Activitat5/img/c2.png)

Ara amb la següent comanda instal·larem la nostre BBDD

![Captura](https://github.com/Shyrkoon/Base-de-dades/blob/master/Activitat5/img/c3.png)

Deshabilitar el SELINUX

![Captura](https://github.com/Shyrkoon/Base-de-dades/blob/master/Activitat5/img/c4.png)

Ara el que tenim que fer és desactivar el Firewall, per tal que no rebutgi les peticions.

![Captura](https://github.com/Shyrkoon/Base-de-dades/blob/master/Activitat5/img/c5.png)

Si ens fixem en la següent captura veiem que el cluster esta format per ell mateix.

![Captura](https://github.com/Shyrkoon/Base-de-dades/blob/master/Activitat5/img/c6.png)

Anem a configurar el fitxer de configuració del Node Princpipal:

![Captura](https://github.com/Shyrkoon/Base-de-dades/blob/master/Activitat5/img/c7.png)

Un cop configurat el node 1, configurem la resta de nodes amb el els mteixos paràmetres.
Encenem el servei en l node prinicpal amb la comanda: systemctl start mysql@bootstrap.service
La resta de servidor tenim que fer-ho amb systemctl start mysql

![Captura](https://github.com/Shyrkoon/Base-de-dades/blob/master/Activitat5/img/c8.png)

Un cop que ho tenim configurat ja podrem veure dins del Mysql que ja ens han sincronitzat i ja tenim el Cluster montat.

![Captura](https://github.com/Shyrkoon/Base-de-dades/blob/master/Activitat5/img/c9.png)

Ara en 

![Captura](https://github.com/Shyrkoon/Base-de-dades/blob/master/Activitat5/img/c10.png)


