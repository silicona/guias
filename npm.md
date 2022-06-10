# NPM

Gestor de paquetes de Node. Utiliza el archivo package.json.

## Ejecución:

Dos opciones:
	: Ejecutar en consola `npm init` para crear el json
	: Escribir aparte package.json y ejecutar `npm install`


[Truco de actualización de dependencias](https://www.campusmvp.es/recursos/post/truco-actualizar-a-la-ultima-las-versiones-de-dependencias-npm-en-package-json.aspx)

## Escribir json

{
  "name": "clientes",
  "version": "0.1.0",
  "devDependencies": {
    "grunt": "~0.4.5",
    "grunt-contrib-jshint": "~0.10.0",
    "grunt-contrib-nodeunit": "~0.4.1",
    "grunt-contrib-uglify": "~0.5.0",
    "grunt-contrib-qunit": "~0.2.0"
  }
}

~ - Instala esa version
^ - Minor: Instala la versión superior dentro de la mayor version actual
>= - Mayor: Instala la version superior o igual
* y "" - Instala la mayor versión disponible

## Comandos
- `npm list -g`: Lista los modules instalados de forma global
- `npm list -g -depth=1`: Lo mismo con el primer nivel
- 
- `npm i -D [nombre de paquete]`: Instala paquete en el proyecto en env development
- `npm i -g [nombre de paquete]`: Instala de manera global
### npm-check-updates

Módulo para comprobar la mayor verison disponible de un paquete.

Instalacion con `npm install npm-check-updates`

Ejecucion con `ncu`


## Grunt

[Bases](http://trip2themoon.com/primeros-pasos-con-grunt-para-disenadores-web/)