# Mac - Apple

## XAMPP

Mac trae un servidor Apache montado por defecto. Puede crear conflicto con el servidor Apache de XAMPP al utilizar los dos el puerto 80.

### Comandos Unix

  - Muestra el directorio actual completo: `pwd`
  - Inicia el servidor Mac: `sudo apachectl start`
  - Detiene el servidor de Mac para que XAMPP utilice el puerto 80: `sudo apachectl stop` 
  - Muestra qué programas utilizan el puerto: `lsof -i -P|grep -i "<puerto a escuchar>"`
  - Muestra qué usuarios utilizan el puerto 80:`sudo lsof -i ':80'` 
  - Busca el paquete en los instalados en local: `ldconfig -p | grep mysqlclient`
  - Muestra el tamaño de archivos y carpetas del directorio actual: `df -sh *`
  - Como df pero mejor: `du -sh *`
  - Devuelve el PID del proceso: `prgrep [nombre_servicio]`
  - Ver todos los procesos: `ps -ax` 
  - Ver proceso concreto: `ps -ax | grep [proceso]` 
  - Termina el proceso del PID: `kill [PID]`
  - Termina todos los procesos del servicio: `killall [nombre_servico]`
  - Da permisos rwxr-xr-x a los archivos de la carpeta. -R hace recursiva la orden para las subcarpetas: `chmod -R 755 *`

## MySQL

En Mac, los archivos de las tablas de MySQL de PHPMyAdmin se guardan en el directorio: /Applications/XAMPP/xamppfiles/var/mysql/

Problema: No se inicia mysql de XAMPP
  - Posiblemente, Mac ha iniciado un servicio mysqld. Elimina todos los procesos anteriores.


## Keychain

Ruta: Aplicaciones/utilidades/acceso a llaveros

### Link simbolicos

Para realizar enlaces en usr/bin/, es necesario entrar primero por la consola del admin con `sudo su`.

  - `ln -s </path/origen/archivo> </path/destino/archivo>`


### Traceroute

Programa de consola que rastrea la ruta web por la que pasa una llamada http.

  - [Artículo para ejecutar en Mac](https://support.hostgator.com/articles/how-do-i-run-a-traceroute-on-a-mac)

## Curl

Recibir las cabeceras del navegador
  - Ejecutar en consola - `curl -I localhost:<puerto, ej 3000>`
  - Obtener ip del router - `curl ifconfig.me`

## Apt

