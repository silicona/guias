# Prestashop

Descargar la ultima version de la página web.

Si no esta instalado php zip, instalarlo con apt-get y reiniciar apache

Crear base de datos para prestashop y usuario asociado.

Descomprimir y acceder a localhost/carpeta_prestashop.

Configurar por navegador.

El programa renombra la carpeta admin por seguridad.

Comprobar permisos de escritura al crear tema hijo y otros.

[Docs oficiales](https://devdocs.prestashop.com/1.7/modules/creation/module-file-structure/#cache-file-config-xml)

## Modulo AutoUpgrade - actualizador de versiones PrestaShop

[Source](https://github.com/PrestaShop/autoupgrade/releases)

¡¡Localhost con XAMPP!!
function `mail` provoca error al pagar - deshabilitar en:
`vendor/swiftmailer/swiftmailer/lilb/classes/Swift/Transport/SimpleMailInvoker.php`

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

### Icono Pestaña

	Template de referencia - /app/Resources/views/base.html.twig
	Imagen - /img/favicon.ico

## Construccion

[parametros por defecto INICIO](https://www.tiendaonlinemurcia.es/editar-plantilla-por-defecto-prestashop/)

### Imágenes
Todos .jpeg o .png, salvo excepciones.
Logotipo - (160~200)x(40~65) px
favicon - .ico 16x16 o 32x32
ps_banner - 1110x214 px
ps_slider - 1111x340 px
producto - 800x800 px
marca de agua - .gif

### Formato de urls

En Param. tienda - tráfico&SEO

	En apartado Formato de enlaces (* - Obligatorio)
		
		Ruta a los productos - 	{category:/}{id}{-:id_product_attribute}-{rewrite}{-:ean13}.html
			Palabras clave: id* , id_product_attribute* , rewrite* , ean13 , category , categories , reference , meta_keywords , meta_title , manufacturer , supplier , price , tags

		Ruta a las categorías - {id}-{rewrite}
			Palabras clave: id* , rewrite , meta_keywords , meta_title

		Ruta a la categoría que tiene el atributo "selected_filter" para el módulo de "Navegación por capas" (blocklayered) - {id}-{rewrite}{/:selected_filters}
			Palabras clave: id* , selected_filters* , rewrite , meta_keywords , meta_title

		Ruta a los proveedores - supplier/{id}-{rewrite}
			Palabras clave: id* , rewrite , meta_keywords , meta_title

		Ruta a la marca - brand/{id}-{rewrite}
			Palabras clave: id* , rewrite , meta_keywords , meta_title

		Ruta a la página - content/{id}-{rewrite}
			Palabras clave: id* , rewrite , meta_keywords , meta_title

		Ruta a la categoría de página - content/category/{id}-{rewrite}
			Palabras clave: id* , rewrite , meta_keywords , meta_title

		Ruta a los modulos - module/{module}{/:controller}
			Palabras clave: module* , controller*

### Twig

Helpers de twig

asset - Apunta a /img

`{{ path('url_nombrada_de_routes_yml', {attr_requerido:valor_requerido}) }}` - Crea la url en el template twig

### Smarty

En plantillas de Smarty (.tpl) - `{debug}` devuelve las variables de la pagina.
`{dump($variableName)}`
`{$var|@print_r}`
`{$var|@debug_print_var}`


```
{* This string is commented out *}

{*
This string is too!
*}
```

### Modulos

[Validador de Modulos de Prestashop (con login)](https://validator.prestashop.com/)

#### AJAX

[ajax dentro de un modulo](https://www.prestashop.com/forums/topic/911760-ajax-request-to-custom-admin-module-controller/)

Turns out there are 2 types of ajax methods:
```
public function ajaxProcessGetBar(){
    // this will be called in combination with postProcess()
    // on your ajax call, if you have submitted $_POST['action'] = 'getBar';  
    // then this will be called.
}

public function displayAjaxGetbar(){
    //this will be called even without the post process, as long as $_POST['ajax'] = 1;
    // on your ajax call, if you have submitted $_POST['action'] = 'getBar'; 
    // notice that you have to change the function name to all lower case.
}
```
 
So, here's what's important to consider:
```
class AdminFooBarController extends ModuleAdminController
{
    public function postProcess()
    {
        return parent::postProcess(); // IF YOU DON'T DO THIS FOR ANY REASON
    }

    public function ajaxProcessGetBar()
    {
        return 'foo'; //THIS WON'T BE FUNCTIONING PROPERLY
    }
}
```

DEVOLVER RESULTADO:
  Utilizar metodo de `ControllerCore::ajaxDie(value, controller, method)`


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

Probar esto - https://stackoverrun.com/es/q/7655091

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

Tambien en Param Avanzados - Rendimiento

### Hooks

[PS 1.7]
En archivo classes/Hooks.php, insertar codigo para detetar los hooks de la pagina y sus parametros. Crear un archivo en la carpeta apropiada (admin o root).

```
$args = array();
foreach($hook_args as $k => $v){

    $valor = (gettype($v) == 'string' || gettype($v) == 'integer') ? $v : gettype($v);

    $args[] = "\t\t" . (string) $k . ": " . $valor;
}

    //dump(debug_backtrace());
$arr = array(
    '---',
    'Nombre: ' . $hook_name,
    "\targs:", implode("\n", $args),
    "\tid_module: " . $id_module,
    "\tarr_return (type): " . gettype($array_return),
    "\tcheck (bool): " . (string) $check_exceptions,
    "\tuse_push (bool):  " . (string) $use_push,
    "\tid_shop (type): " . (string) $id_shop,
    "\tchain (bool): " . (string) $chain,
    '---'
);

file_put_contents('hooks_exec.txt', PHP_EOL.implode("\n", $arr), FILE_APPEND | LOCK_EX);
```

### Notice

Por php7.1 sale un Notice cunado `tempnam()` crea un archivo en el sistema. Probar a poner @ delante para anular el aviso.

## Tests

### Puppeteer

[Docs Prestashop](https://github.com/PrestaShop/PrestaShop/blob/develop/tests/puppeteer/README.md)

### Modulos

## ERRORES 

Fallo al recargar lista de modulos desde curl api.prestashop.com
En `classes/controller/AdminController.php::initTabmoduleList`, 2177 al hacer refresh con la url de la api.

### Compra en XAMPP localhost

El envio de email desde local entorpece el proceso de pago. Para inhabilitarlo:
Rastrear el envio del email con el pedido:
    classes/PaymentModule - Poner DEBUG_MODE=true y seguir el rastro de logs.
    PS 1.7.6.4
    classes/PaymentModule::validateOrder, lin 555 New Order History() -> addWithemail()
    classes/order/OrderHistory::addWithemail -> sendEmail()
    classes/order/OrderHistory::sendEmail, lin 539 Mail::Send()
    classes/Mail::send
        lin 365 Swift_Mailer - 
            vendor/swiftmailer/swiftmailer/lib/classes/Swift/Mailer.php
        lin 595 $swift -> send - Provoca que Localhost no devuelva nada
            Cambiar por $send = true para pruebas y localhost

## Domain\Repository

En Prestashop
  - Doctrine\DBAL\Query\QueryBuilder - vendor/doctrine
  - Doctrine\DBAL\Driver\PDOStatement - vendor/doctrine

[PDO fetch y otros](https://www.php.net/manual/en/pdostatement.fetch.php)
[PDO docs constantes](https://www.php.net/manual/es/pdo.constants.php)
## Forms

[Docs Presta](https://devdocs.prestashop.com/1.7/development/architecture/migration-guide/forms/crud-forms/)

  - FormDataProvider - Form\DataProvider\MyFormDataProvider + registro en services.yml
    - Inyecta queryBus como getData()
  - FormType - Form\Type\MyFormType
  - FormBuilder - registro en services.yml con args(MyFormType, MyFormDataProvider)
  - FormDataHandler - Form\DataHandler\MyFormDataHandler + registro en services.yml
    - Inyecta commandBus en create() y update()

## Grids

[docs Presta Grid](https://devdocs.prestashop.com/1.7/development/components/grid/)
[Docs Presta Filters](https://devdocs.prestashop.com/1.7/development/components/grid/tutorials/work-with-search-form/in-1-7-5/)

  - GridDefinitionFactory - Grid\Definition\Factory\MyGridDefinitonFactory + registro en services.yml (por filters)
  - GridQuery - Grid\Query\MyGridQuery
  - GridSearchSearchCriteria - GRID\Search\SearchCriteria\MySearchCriteria


