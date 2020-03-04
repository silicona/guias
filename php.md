# PHP

## SimpleXML

[Tutorial simple](https://diego.com.es/tutorial-de-simplexml)

### Detectar elementos repetidos en array


    $repeated = array_filter(array_count_values($array_numerico), function($count) {
        return $count > 1;
    });
    foreach ($repeated as $key => $value) {
        echo "Clave '$key' está repetido $value veces<br />";
    }

### Extensiones

#### INTL

Si la instalacion de php es la del OS (`/usr/local/php`):
 : Ejecutar `brew install php[version sin puntos]-intl`

Problema con Prestashop y Magento en la instalación - extension intl no está instalada.

Necesario tener instalado Xcode y autoconf (`brew install autoconf`)

El path de php debe ser el de XAMPP:
  : Ejecutar `which php` - Debe apuntar a /Applications/XAMPP/xamppfiles/bin/php
  : Modificar path si no - `PATH="/Applications/XAMPP/xamppfiles/bin:${PATH}"`
  : Comprobar version php - `php -v`
  : Comprobar icu instalado - `brew install icu4c`
  : Instalar por pecl:
    Ejecutar `sudo pecl update-channels`
    Ejecutar `sudo pecl install intl`
  : Comprobar instalación correcta - `php -m | grep intl` (Devuelve intl)

En caso de que falle
  : Descargar la versión de php desde php.net en version `.tar.gz`
  : Descomprimir o ejecutar `tar -xzvf php-[version].tar.gz`
  : Acceder a path/to/php-[version]/ext/intl/
  : Contruir la extension de PHP:
    Ejecutar - `/Applications/XAMPP/bin/phpize`
    Ejecutar - `./configure --enable-intl --with-php-config=/Applications/Xampp/bin/php-config --with-icu-dir=/Applications/XAMPP/xamppfiles/`
    Ejecutar - `make`
    Ejecutar - `sudo make install`
  : Añadir a php.ini `extension=intl.so`
  : Reiniciar XAMPP
  : Comprobar instalación correcta - `php -m | grep intl` (Devuelve intl)

Si tampoco reconoce la extensión intl en la instalación de Prestashop, comprobar las extensiones de XAMPP:
  : Acceder a `/Applications/XAMPP/xamppfiles/lib/php/extensions/[version de php]/`
  : Ademas de archivos .a y .so, debería estar intl.so.
  : Clonar intl.so con extensión .a
  : Reiniciar y actualizar instalación
  : Comprobar instalacion en `localhost/dashboard/phpinfo.php` - La extensión Intl debería salir en su lugar.


