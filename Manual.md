# CURSO DE MYSQL

## DATOS DE CONEXIÓN
### MAQUINA VIRTUAL
* IP VM: 192.168.56.101
* usuario: root
* pass: pomv5000
### BBDD
* usuario: exploit
* pass: exploit

## CONECTARSE A LA BASE DE DATOS DEL SISTEMA
/soft/mys57/bin/mysql -u exploit -pexploit
 
## ARBORESCENCIA
<pre>
/soft/mys55/
		/bin/
				/mysql
				mysqlhotcopy
				mysqldump
				mysqlbinlog
			/fileso/
				profile => 100% psa. Script de menú eso_001.sh se almacena aquí
			/include
			/lib
			/man
			/share

/users --> no crezca. limitado a 30 gigas => Tenemos los datos.
	/mys50
		/data/
			my.cnf
			/mysql
			/mibase --> creamos un link a /log
		/logs/
			general.log
			error.log
			slow-queries.log
		/socket
	/prd00
		/base
		/web
			/html
				index.php
			/uploads
			/inc
		/scripts

/logs --> antes se guardaban en users ahora se crean en /log.
</pre>
Schemas = Directorios</br>

Al crear un bbdd creamos un directorio</br>
Tablas --> (.frm files)</br>
MyISAM: frm + MYD + MYI</br>
InnoDB: frm + ibd + (ibdata)</br>

BBDD de sistema: mysql</br>
Información sobre usuarios, privilegios, contenidos de ayuda, etc.</br>

## INSTALACIÓN MYSQL

Fichero de configuración MYSQL en el servidor, es común para todos los proyectos instalados en el servidor.</br>
Se puede localizar en /users/mys50/data/my.cnf</br>

## CAMBIOS DE VARIABLES

Mostrar las variables  valores del servidor MYSQL</br>
SHOW VARIABLES;</br>
show variables like "%connections%";</br>
me da max_connections=150</br>
### EN CALIENTE (TEMPORAL)
set @@global.max_connections=200</br>
ahora me dan max_connections=200</br>
esta es una medida en caliente que solo se mantiene hasta que mysql se reinicia.</br>

### EN FRIO (PERMANENTE)
Si queremos hacer esta medida permanente debemos modificar nuestro my.cnf</br>
/users/mys57/data/my.cnf</br>
max_connections = 200</br>

menu eso_001.sh</br>
/soft/mys57/fileso/MENU.sh</br>
 
## LOGS
### TIPOS DE LOG
* **"General log" (general query log)**: es el log que guarda todos los "statements" que el servidor recive desde sus clientes. Escirbe absolutamente todo lo que se hace. Se activa cuando se hace una instalación nueva y luego se desactiva pero en PSA nunca se desactiva con lo que se va llenando de logs el espacio.
* **"Log binario" (binary log)**: Guardar solamente los "statements" que modifican datos. Log interesante pq solo escribe los cambios que se hacen en la bbdd. Haces copia de la bdd a las 2 de la mañana, si haces consultas no escribe nada pero si haces algún cambio guarda esas modificaciones en el log. Puedes coger la copia de la bbdd y coger el log bin con los cambios que se han realizado.
* **"Log de consultas lentas" (slow query log)**: Contiene un registro de consultas que precisaron mucho tiempo para ejecutarse. Solo guardan las consultas que se realizan a las bbddd. Sirve para cuando realizamos una busqueda y tarda mucho en mostrar la información, es donde podemos depurar porque está ocurriendo esta lentitud. (Ver si los datos los tiene que cruzar con muchas tablas, etc).
* **"Log de error" (error log)**: Guarda mensajes de diagnóstico del servidor sobre los "start-ups", "shut-downs" y condiciones anormales que se puedan producir.
* **"Log bin index (log-bin.index)**":

### ROTACIÓN DE LOGS



