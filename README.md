# CursoMySQL
### Algunos trucos para MySQL

1. Conectarse al contenedor con USER/PASSWORD:  $ docker exec -i CONTAINER mysql -u USER -pPASSWORD
2. Conectarse a la base de datos en el contenedor con USER/PASSWORD: $  docker exec -i CONTAINER mysql -u USER -pPASSWORD DATABASE
3. Ejecutar script en el contenedor con USER/PASSWORD: $ docker exec -i CONTAINER mysql -u USER -pPASSWORD DATABASE < SCRIPT
4. Pasar la entrada como un script a un contenedor: $ docker exec -i CONTAINER mysql -u USER -pPASSWORD DATABASE << EOF
```
$ INPUT
$ EOF
```
5. Pasar un comando como entrada a un contenedor:  $ docker exec -i CONTAINER mysql -u USER -pPASSWORD DATABASE <<<  "COMMAND"

* Consultar bases de datos: SHOW databases;
* Consultar tablas: SHOW tables;
* Eliminar tabla: DROP TABLE TABLENAME;
* Eliminar base de datos: DROP DATABASE DATABASE;

* Añadir usuario: GRANT SELECT ON *.* TO 'USER'@'localhost' IDENTIFIED BY 'PASSWORD';
* Darle permisos a un usuario: GRANT ALL PRIVILEGES ON *.* TO 'USER'@'localhost' IDENTIFIED BY 'PASSWORD';
* Dar acceso externo a un usuario: GRANT ALL PRIVILEGES ON *.* TO 'USER'@'%' IDENTIFIED BY 'PASSWORD';
* Comprobar usuarios: SELECT user FROM mysql.user GROUP BY user;
* Comprobar usuarios y puntos de acceso: SELECT user,host FROM mysql.user;
* Eliminar usuario: DELETE FROM mysql.user WHERE user = 'USER';
* Contar líneas de una tabla:  SELECT COUNT(*) FROM TABLE;

### Anotaciones importanes:
* Al lanzar un docker exec se usa la opción -i únicamente, y no la típica -it, ya que no queremos crear una "sesión con terminal"
* La contraseña debe ir pegada a la opción -p, si se separa mysql entiende que se va a introducir una contraseña por separado, y que la introducida en el comando es, en realidad, una Base de Datos
* Todas las acciones de: añadir/borrar usuarios, dar permisos, consultar tablas/bases de datos, etc… se puede realizar pasando un script al contenedor, como se ve en el punto 3.
