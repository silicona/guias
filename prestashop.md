# Prestashop

Descargar la ultima version de la página web.

Si no esta instalado php zip, instalarlo con apt-get y reiniciar apache

Crear base de datos para prestashop y usuario asociado.

Descomprimir y acceder a localhost/carpeta_prestashop.

Configurar por navegador.

El programa renombra la carpeta admin por seguridad.

Comprobar permisos de escritura al crear tema hijo y otros.


## Tema hijo - A partir de 1.7

[blog origen](https://www.4webs.es/blog/crear-tema-hijo-prestashop-1-7)


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

