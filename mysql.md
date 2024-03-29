  # MySQL

## Comandos

### Bases y Tablas

Crear Base de datos
  : `CREATE database tdd_intro CHARACTER SET utf8 COLLATE utf8_general_ci;`
  : `CREATE DATABASE IF NOT EXISTS api_sinatra CHARACTER SET utf8 COLLATE utf8_general_ci;`

Borrar Base de datos
  : `DROP DATABASE <nombre_base>;`
  : Accion por comandos si el directorio no está vacio
	:Carpeta en Mac - `/Applications/XAMPP/xamppfiles/var/mysql/`
	: `rm -r <nombre_base>`

Operar con una Base de datos
  : `use videoclub;`

Mostrar las Bases de datos
	: `SHOW databases;`

Operar con una Base de datos
	: `use videoclub;`

Mostrar las tablas de una BD
	: `SHOW tables;`

Muestra la estructura de una tabla
	: `DESCRIBE peliculas;`

Muestra las constantes Constraint de una tabla
	: `select * from information_schema.table_constraints where table_name = "avispas";`

Crear Tablas
	: `CREATE table peliculas ( id int auto_increment, titulo varchar(20) NOT NULL, direccion varchar(200) DEFAULT '', autor varchar (200), estreno year(4), sinopsis text, primary key (codigo));`

Vacia la tabla y la vuelve a crear
	: `TRUNCATE table peliculas;`

Renombrar tabla
	: `ALTER TABLE amigos RENAME contactos;`
	: `RENAME TABLE amigos TO contactos;`

Comprobar tabla
	: `CHECK TABLE peliculas FAST QUICK;`
	: `CHECK TABLE peliculas EXTENDED;`

Añadir indice
	  : `ALTER TABLE peliculas ADD INDEX <nombre_indice>(<nombre_campo>);`

Añadir Foreing key con alter (No funciona si la tabla tiene datos)
	: `ALTER TABLE peliculas ADD FOREIGN KEY (<nombre_campo>) REFERENCES <otra_tabla>(<nombre_campo>)`
	: `ALTER TABLE peliculas ADD CONSTRAINT FK_NombreKey FOREIGN KEY (<nombre_campo>) REFERENCES <otra_tabla>(<nombre_campo>)`

Añadir campo a tabla
	: `ALTER TABLE (nombre_tabla) ADD COLUMN <nombre_columna> <tipo> AFTER <nombre_columna>;`
	: `ALTER TABLE peliculas ADD COLUMN <campo_nuevo> varchar(30);`

Borrar campo de tabla (no borra indices si solo hay uno en la tabla)
	: `ALTER TABLE peliculas DROP dirección, DROP estreno;`

Modificar campos
	: `ÀLTER TABLE peliculas MODIFY estreno SMALLINT UNSIGNED;`

Modificar el atributo de campo DEFAULT
	: `ALTER TABLE peliculas ALTER autor SET DEFAULT 'Varios';`

Borrar el atributo de campo Default
	: `ALTER TABLE peliculas ALTER autor DROP DEFAULT;`

Exportar tabla y estructura
	: `mysqldump -u root -p nombre_base > archivo.sql` - (Pide la pass del usuario)

Exportar una tabla a un archivo
	: `mysqldump –opt -h <servidor> -u <usuario> -p <basededatos> <tabla> > <archivo.sql>`

Importar datos desde archivo.sql
	: `mysql -u <usuario> -p <basededatos> < <archivo.sql>`



### Gestión de registros

Obtener registros de la Base de Datos
	: `SELECT * FROM peliculas WHERE id = $id ORDER BY titulo DESC;`
	: `SELECT titulo, autor FROM peliculas WHERE estreno >= '1980';`
	: `SELECT titulo, autor FROM peliculas WHERE estreno BETWEEN 1980 AND 2000;`
	: `SELECT * FROM libros WHERE SELECT titulo FROM peliculas WHERE NOT titulo = 'Amanecer zulu';`     
	: `SELECT titulo FROM peliculas WHERE direccion LIKE "%Coppola%";`
	: `SELECT DISTINCT titulo FROM peliculas WHERE direccion REGEXP "Coppola";`
	: `SELECT * FROM 4887_anuncios WHERE telefono IN (SELECT telefono from 4887_telefonos_inmobiliarias); - Obtiene los registros de anuncios con el telefono incluido en la tabla telefonos_inmobiliarias;`

Crear un rgistro en la Base de datos
	: `INSERT INTO peliculas(titulo, direccion, autor, estreno, sinopsis) VALUES ('{$nombre}', '{$direccion}', '{autor}', '{$estreno}', '{$sinopsis}');`

SQL para ordenar las llamadas por primer dia de la semana

	SELECT FROM_DAYS(TO_DAYS(f_llamada) -MOD(TO_DAYS(f_llamada) -1, 7)) AS dia_inicio_semana,
			COUNT(id_llamada) AS num_llamadas
				FROM 4887_llamadas
				WHERE id_usuario = ' . $id_usuario . '
					GROUP BY FROM_DAYS(TO_DAYS(f_llamada) -MOD( TO_DAYS( f_llamada ) -1, 7) )
					ORDER BY FROM_DAYS(TO_DAYS(f_llamada) -MOD( TO_DAYS( f_llamada ) -1, 7) ) ASC';

Encontrar los id_anuncio con más de un id__anuncio_seguimiento (pry), ordenados por id_anuncio
	: `SELECT id_anuncio, count(id_anuncio_seguimiento) FROM 'tabla_seguimientos' GROUP BY id_anuncio HAVING count(id_anuncio_seguimiento) > 1`;

Encontrar los id_soporte que tienen el id_concurso repetido en otro registro
	: `SELECT id_soporte, count(id_concurso) as repe FROM 4887_soportes WHERE id_tipo_soporte = 0 group by id_concurso having repe > 1`

Crear un registro en la Base de datos
	: `INSERT INTO peliculas(titulo, direccion, autor, estreno, sinopsis) VALUES ('{$nombre}', '{$direccion}', '{autor}', '{$estreno}', '{$sinopsis}');`

Actualizar un registro
	  : `UPDATE peliculas SET titulo = '{$titulo}', direccion = '{$direccion}', autor = '{$autor}', estreno = '{$estreno}', sinopsis = '{$sinopsis}' WHERE id = $id;`

Reemplazar un registro (puede repitir campos Primary y Unique)
	  : `REPLACE INTO peliculas VALUES (23, 'Amanecer Púrpura', 'Charles Bukowsky', '1910', 'Sinopsis de ejemplo.');`

Borrar un registro
	: `DELETE FROM peliculas WHERE id = $id;`
	: `DELETE FROM peliculas LIMIT 3;`
  
---

### Usuarios de MySQL

	Crear Usuario (opcion 1)
	  : `GRANT ALL ON videoclub.* TO 'usuario'@'localhost' IDENTIFIED BY 'pass';`

	Listar todos los usuarios de un servidor MySQL
	  : `SELECT User from mysql.user;`
	  : `select user,host from mysql.user;`

	Ver los privileguios de un usuario
	  : `SHOW GRANTS FOR [usuario]@[host];`
	  : `SHOW GRANTS FOR shilum@localhost;`
	  : `select user,host,select_priv from mysql.db`

	Usuarios con acceso a cada base de datos
	  : `SELECT u.User,Db FROM mysql.user u,mysql.db d WHERE u.User=d.User;`

	Refrescar Tabla mysql de permisos
	  : `FLUSH PRIVILEGES;`

	Obtener nuestro usuario (conectado)
	  : `SELECT CURRENT_USER();`


## PHPMyAdmin

Los problemas de permisos con PhpMyAdmin en local pueden provenir de los usuarios root y phpmyadmin de la base de datos MySql.

Verificar que los permisos de ambos usuarios son totales.

Procedimiento:

entrar en mysql con perfil de administrador (sudo su). Cuando se ve el prompt del admin, ejecutar `mysql`.
Dentro de mysql, agregar todos los permisos al usuario con `GRANT ALL ON *.* TO 'usuario'@'localhost' IDENTIFIED BY 'pass';`

## Problemas de acceso

  Error: Can't connect to local MySQL server through socket '/tmp/mysql.sock'
    - Ejecutar `mysql -u root -p -h 127.0.0.1`
    
### Incompatibilidad mysql nativo y xampp
Producido al utilizar WorkBench, que solo acepta MySql Server, con MariaDb de Xampp

Normalmente, xampp y su MySql(MariaDB) estan en la carpeta xampp.
El MySql nativo puede haber sido instalado en /usr/local/mysql[linksim]/

  Error: Can't connect to local MySQL server through socket '/tmp/mysql.sock'
    - Ejecutar `/usr/local/mysql[linksim]/support-files/mysql.server start` para iniciar el servidor en 3306
    - Ejecutar `/usr/local/mysql/bin/mysql` para conectar a mysql ó
    - Ejecutar WorkBench sobre la conexion en puerto 3306

Es posible haya que utilizar `sudo`.

## Enlaces de referencia

  * Ver la [Documentacion de MySQL](https://dev.mysql.com/doc/)

  * Desde [linuxito](https://www.linuxito.com/gnu-linux/nivel-medio/544-como-listar-todos-los-usuarios-en-mysql)

  * Ver Crear Base de datos en [la web de Aner Barrena](http://www.anerbarrena.com/create-database-mysql-4991/)

  * Como crear usuarios de MySql en [Cambrico.net](http://cambrico.net/mysql/como-crear-un-usuario-en-mysql-3-formas-diferentes)


## Instalacion de wordpress

Ver la instalación basica de [Wordpress en Ubuntu 16](https://www.digitalocean.com/community/tutorials/como-instalar-wordpress-con-lamp-en-ubuntu-16-04-es)


## Cómo crear un usuario en MySQL: 3 formas diferentes


### La forma clásica, con la sentencia GRANT

Utilizando la sentencia GRANT podemos crear un usuario a la par que otorgarle uno o varios privilegios sobre los objetos de una base de datos, o la base de datos completa.

	mysql> GRANT ALL ON videoclub.* TO 'adolfo'@'localhost' IDENTIFIED BY 'pass_adolfo';
	mysql> GRANT SELECT, INSERT ON test.* TO 'adolfo'@'localhost' IDENTIFIED BY 'pass_adolfo';
	mysql> USE test;	>>	Database changed
	mysql> SELECT * FROM frutas;


| nombre    | color    |
|:---------:|:--------:|
| fresa     | rojo     | 
| manzana   | verde    | 
| uva       | verde    |


### La sentencia CREATE USER

A partir de la versión MySQL 5.0.2 existe la posibilidad de crear usuarios sin necesidad de asignarles privilegios, utilizando la sentencia CREATE USER.

	mysql> CREATE USER 'fernando'@'localhost' IDENTIFIED BY 'fer_pass';

Los privilegios necesarios para ejecutar la sentencia CREATE USER son `CREATE USER` o bien `INSERT` en la base de datos mysql. El usuario recién creado no tiene privilegio alguno, por lo que deberemos asignarle permisos utilizando sentencias GRANT (esta vez sin la cláusula IDENTIFIED BY).

### Modo hardcore: insertando en la tabla users

Mucho cuidado con esta base de datos, ya que contiene toda la información de usuarios y permisos.

Ejemplo de creación del usuario mariano usando INSERT en nuestra base de datos. Nos conectamos con un usuario con privilegios, en este caso root, y seleccionamos la base de datos mysql mediante la sentencia USE.

	mysql> USE mysql;  >>	Database changed
	mysql> INSERT INTO user VALUES('localhost','mariano',PASSWORD('pass_mariano'),'Y','Y',        'N','N','N','N','N','N','N','N','N','N','N','N','N','N','N','N','N','N','N','N','N',        'N','N','N','','','','',0,0,0,0);		>>  Query OK, 1 row affected (0,00 sec)

Es necesario llamar a la función PASSWORD() para almacenar el password codificado, en los otros casos, el IDENTIFIED BY se encarga de hacer la codificación.

En este caso se le dan permisos globales de INSERT y SELECT, para saber a qué corresponde cada columna, se puede hacer un DESCRIBE user.

	mysql> DESCRIBE user;

| Field                 | Type              | Null | Key | Default | Extra |
|:---------------------:|:-----------------:|:----:|:---:|:-------:|:-----:|
| Host                  | char(60)          | NO   | PRI |         |       | 
| User                  | char(16)          | NO   | PRI |         |       | 
| Password              | char(41)          | NO   |     |         |       | 
| SELECT_priv           | enum('N','Y')     | NO   |     | N       |       | 
| Insert_priv           | enum('N','Y')     | NO   |     | N       |       | 
| Update_priv           | enum('N','Y')     | NO   |     | N       |       | 
| Delete_priv           | enum('N','Y')     | NO   |     | N       |       | 
| Create_priv           | enum('N','Y')     | NO   |     | N       |       | 
| Drop_priv             | enum('N','Y')     | NO   |     | N       |       | 
| Reload_priv           | enum('N','Y')     | NO   |     | N       |       | 
| Shutdown_priv         | enum('N','Y')     | NO   |     | N       |       | 
|	(...)               |                   |      |     |         |       |


Para asignar privilegios a bases de datos específicas o tablas específicas, se debe usar GRANT.

Utilizando este método, tenemos que forzar que se refresquen las tablas de permisos usando FLUSH PRIVILEGES.

	mysql> FLUSH PRIVILEGES;


### Otras consideraciones

También se pueden crear usuarios desde la herramienta visual MySQL Administrator, que forma parte de las GUI Tools que ofrece gratuitamente MySQL y se pueden descargar desde aquí. (Es multiplataforma, pero en Mac funciona bastante mal)

Para saber con qué usuario estamos conectados en este momento, podemos usar la función CURRENT_USER() o USER().

	mysql> SELECT CURRENT_USER();


	| CURRENT_USER()   |
	|:----------------:|
	| adolfo@localhost | 


Al crear un usuario, se define el contexto desde el que se puede conectar, por ejemplo 'adolfo'@'localhost' solamente se puede conectar desde el mismo servidor de la base de datos.

Para crear usuarios que se puedan conectar desde varias máquinas, se puede crear un usuario por cada máquina o usar el comodín '%', el usuario 'adolfo'@'%' se podría conectar desde cualquier máquina, y el usuario 'fernando'@'192.168.1.%' se podría conectar desde máquinas con una dirección IP comprendida entre 192.168.1.1 y 129.168.1.255.


	GRANT SELECT, INSERT ON test.* TO 'adolfo'@'%' IDENTIFIED BY 'pass_adolfo';
	CREATE USER 'fernando'@'192.168.1.%' IDENTIFIED BY 'fer_pass';

En el caso de que estemos realizando la creación de un usuario mediante el método INSERT y nos aparezca el siguiente error:

	**ERROR 1136 (21S01): Column count doesn't match value count at row 1**

La razón es que algunas de las columnas de la tabla user no tienen valor por defecto (por ejemplo ssl_type), y no las hemos informado todas, es necesario hacerlo.


## SQLs

### Funciones

Obtener informacion de campos de una tabla
	
	Problema - Repite algunos campos y genera error en PhpMyAdmin
	`SELECT column_name FROM information_schema.columns WHERE table_name = "4887_usuarios"`

	No way
	`SELECT c.name FROM sys.columns c JOIN sys.tables t ON c.object_id = t.object_id WHERE t.name = "4887_usuarios"`

#### Fechas (SQL Server)

`NOW()` - Devuelve el datetime actual en formato mysql (yyyy-mm-dd hh:mm:ss)

`CURDATE()` - Devuelve el dia actual en formato mysql (yyyy-mm-dd)

`CURTIME()` - Devuelve la hora actual en formato mysql (hh:mm:ss)

`FROM DAYS(0000000)` - Devuelve una fecha mysql desde un valor numerico en dias desde el año 0

`TO_DAYS('yyyy-mm-dd')` - Devuelve el numero de dias desde el año 0 de una fecha mysql

#### MOD(a, b)

Devuelve el módulo (resto de división) de a/b

Ejemplos de sql:
  : Listar registros repetidos - `SELECT campo1 FROM tabla WHERE campo_id = id GROUP BY campo1 HAVING COUNT(*) > 1`
  : Listar registros unicos - `SELECT campo1 FROM tabla WHERE campo_id = id GROUP BY campo1 HAVING COUNT(campo1) = 1`
  : Lista soportes con campo repetido y campo 2 - 

	select id_soporte from 4887_soportes_detalles 
	where id_soporte IN( 
		SELECT id_soporte FROM 4887_soportes_detalles 
			GROUP BY id_soporte having count(*) > 1 
		) AND id_usuario = 4

Fin de Archivo
