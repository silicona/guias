# Mac - Apple

## XAMPP

Mac trae un servidor Apache montado por defecto. Puede crear conflicto con el servidor Apache de XAMPP al utilizar los dos el puerto 80.

### Comandos Unix

`sudo apachectl start` - Inicia el servidor Mac.

`sudo apachectl stop` - Detiene el servidor de Mac para que XAMPP utilice el puerto 80.

`lsof -i -P|grep -i "<puerto a escuchar>"` - Muestra qué programas utilizan el puerto.

`sudo lsof -i ':80'` - Muestra qué usuarios utilizan el puerto 80

`ldconfig -p | grep mysqlclient` - Busca el paquete en los instalados en local

`df -sh *` - Muestra el tamaño de archivos y carpetas del directorio actual

`du -sh *` - Como df pero mejor.


## MySQL

En Mac, los archivos de las tablas de MySQL de PHPMyAdmin se guardan en el directorio: /Applications/XAMPP/xamppfiles/var/mysql/

## Keychain

Ruta: Aplicaciones/utilidades/acceso a llaveros

### Link simbolicos

Para realizar enlaces en usr/bin/, es necesario entrar primero por la consola del admin con `sudo su`

`ln -s </path/origen/archivo> </path/destino/archivo>`


### Traceroute

Programa de consola que rastrea la ruta web por la que pasa una llamada http.

[Artículo para ejecutar en Mac](https://support.hostgator.com/articles/how-do-i-run-a-traceroute-on-a-mac)
