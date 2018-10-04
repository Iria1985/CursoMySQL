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
/soft/mys55/<br/>
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

Schemas = Directorios

Al crear un bbdd creamos un directorio
Tablas --> (.frm files)
MyISAM: frm + MYD + MYI
InnoDB: frm + ibd + (ibdata)

BBDD de sistema: mysql
Información sobre usuarios, privilegios, contenidos de ayuda, etc.

INSTALACIÓN MYSQL
==================
Fichero de configuración MYSQL en el servidor, es común para todos los proyectos instalados en el servidor.
Se puede localizar en /users/mys50/data/my.cnf

CAMBIOS DE VARIABLES
======================
Mostrar las variables  valores del servidor MYSQL
SHOW VARIABLES;
show variables like "%connections%";
me da max_connections=150
set @@global.max_connections=200
ahora me dan max_connections=200
esta es una medida en caliente que solo se mantiene hasta que mysql se reinicia.

si queremos hacer esta medida permanente debemos modificar nuestro my.cnf
/users/mys57/data/my.cnf
max_connections = 200

menu eso_001.sh
/soft/mys57/fileso/MENU.sh
 


