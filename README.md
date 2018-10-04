192.168.56.101
root 
pomv5000

ARBORESCENCIA
=============
/soft/mys55/
            /bin/
				mysql
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

Mostrar las variables  valores del servidor MYSQL
SHOW VARIABLES;
