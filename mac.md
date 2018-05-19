# Mac - Apple

## XAMPP

Mac trae un servidor Apache montado por defecto. Puede crear conflicto con el servidor Apache de XAMPP al utilizar los dos el puerto 80.

### Comandos

`sudo apachectl start` - Inicia el servidor Mac.

`sudo apachectl stop` - Detiene el servidor de Mac para que XAMPP utilice el puerto 80.

`lsof -i -P|grep -i "<puerto a escuchar>"` - Muestra qué programas utilizan el puerto.

`sudo lsof -i ':80'` - Muestra qué usuarios utilizan el puerto 80


## MySQL

En Mac, los archivos de las tablas de MySQL de PHPMyAdmin se guardan en el directorio: /Applications/XAMPP/xamppfiles/var/mysql/

## Keychain

Ruta: Aplicaciones/utilidades/acceso a llaveros