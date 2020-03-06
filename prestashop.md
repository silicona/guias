# Prestashop

Descargar la ultima version de la página web.

Si no esta instalado php zip, instalarlo con apt-get y reiniciar apache

Crear base de datos para prestashop y usuario asociado.

Descomprimir y acceder a localhost/carpeta_prestashop.

Configurar por navegador.

El programa renombra la carpeta admin por seguridad.

Comprobar permisos de escritura al crear tema hijo y otros.


## Tema hijo - A partir de 1.7

[blog origen - error](https://www.4webs.es/blog/crear-tema-hijo-prestashop-1-7)

[blog tema hijo completo](https://www.jose-aguilar.com/blog/como-crear-un-tema-hijo-en-prestashop-1-7/)

Para crear el child theme, nos vamos a la carpeta “Prestashop/themes“. 

Creamos una nueva carpeta con un nombre diferente, por ejemplo “child-theme” que contenga tres archivos: 
  : config
  : theme.yml
  : preview.png (este archivo será la captura mostrada en el backend y hará referencia al theme).

Editar theme.yml

parent: classic (nombre del padre)
name: hijo-classic
display_name: hijo-classic (para backend)
version: 1.0.0
autor: Name: “xxxxx”
Email: “xxxx@xxxxx.com”
url: “http://www.xxxxxx.com

no podemos olvidarnos de eliminar el símbolo “#” donde aparece escrito “use_parent_assets:true” para que esto funcione. Es una sub entrada de “Assets” para definir si quieres usar CSS y JS del tema padre (true) o no (false).



## Construccion

[parametros por defecto INICIO](https://www.tiendaonlinemurcia.es/editar-plantilla-por-defecto-prestashop/)

### Extension INTL no cargada

Problema en el paso de la Compatibilidad del sistema

#### Utilizando XAMPP (localhost)

You have to build intl-extension from php source code on your own.
If you have some experiences using the terminal it won't be hard to do.

First make sure you installed Xcode and started it at least once to finish installation and accept license agreement.
Download latest version of autoconf from http://ftp.gnu.org/gnu/autoconf/autoconf-latest.tar.gz. Its a prerequisite to build php modules which is not shipped with macOS.
Extract the file and open a terminal in macOS and open the extracted folder using cd command.
Afterwards use commands:
./configure
make
sudo make install (your password is required, make sure you are an admin user in macOS)

Download the version of php you use in xampp from php.net.
Extract it and open the extracted folder in a terminal using cd.
Change to subfolder ext/intl.
Run these commands to build the extension:
`/Applications/XAMPP/bin/phpize`
`./configure --enable-intl --with-php-config=/Applications/XAMPP/bin/php-config --with-icu-dir=/Applications/XAMPP/xamppfiles/`
`make`
`sudo make install` (password required)
Delete all files you downloaded and also the extracted folders.
Add to php.ini file in xampp/etc folder line
extension="intl.so"

Reiniciar XAMPP
ejecutar `php -v` - No debe dar error de extension no disponible


## Acceso

Administracion - Acceder por la url BASE_URL/nombre_tienda/admin

xcache.so, pdo.so, pdo_sqlite.so, mongo.so, memcache.so, pdo_mysql.so

## Debug

En config/defines.inc.php: `define('_PS_MODE_DEV_', true);`
