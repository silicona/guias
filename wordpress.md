# Wordpress

[Instalacion en Ubuntu](https://www.digitalocean.com/community/tutorials/como-instalar-wordpress-con-lamp-en-ubuntu-16-04-es)

## Localhost

Dar permiso a Lamp a la carpeta del blog

`sudo chown -R usuario:grupo /raiz/hasta/wp`

Dar permiso a los archivos

`sudo chmod -R 774 /raiz/hasta/wp`


## Migrar de local a remoto

[web orig](https://www.gianoliveira.com/wordpress-de-local-a-remoto.html)

Pasos
  : Exportar la bbdd.
  : Sustituir http://localhost/wordpress por http://www.tudominio.com en el sql.
  : Ajustar wp-config.php con los valores de la bbdd de producción.
  : Volcar todos los archivos de la carpeta local por FTP.


## Errores

Url del sitio: Modificar en tabla wp-options las dos primeras entradas.

[10 errores comunes](http://blog.hostdime.com.co/10-errores-mas-comunes-de-wordpress-con-las-soluciones/)


## Tema hijo

Crear style.css con:

	/*
	   Theme Name: Divi Hijo
	   Theme URI: http://www.oclemconsultoria.com/
	   Version: 1
	   Description: Tema hijo del tema Divi de wordpress
	   Author: OclemInformatica
	   Author URI: https://www.ocleminformatica.com
	   Template: Divi
	*/
	@import url("../Divi/style.css");

Crear archivo screenshot.jpg con imagen para el index de Temas.

