# Symfony

config - Contains... configuration of course!. 
You will configure routes, services and packages. 

src - All your PHP code lives here. 
templates - All your Twig templates live here. 
bin - The famous bin/console file lives here (and other, less important executable files). 
var - This is where automatically-created files are stored, like cache files (var/cache/) and logs (var/log/). 
vendor - Third-party (i.e. "vendor") libraries live here! These are downloaded via the Composer package manager. 
public - This is the document root for your project: you put any publicly accessible files here.

Extensión annotations instalada de serie 
Rutas en controlador Extensión symfony/asset instalada de serie
Funcion de Twig asset()

## Composer
Instalar paquetes necesarios con --dev para añadirlos al json de configuracion - `composer require [nombre_paquete] --dev`


## NPM

Instalar encore, jquery y otras librerias de JS con npm: `npm install --save [libreria]`

Se instalan en /node_modules

## ORM - Doctrine

orm-pack instalado de serie
maker-bundle instalado de serie

Problemas:
No puede encontrar el driver: Instalar el modulo mysql en la version actual de php - `sudo apt-get install php[version~7.1]-mysql`

Confirmacion: `php -i | grep mysql`

### Configurar y poblar Bases de datos
Creacion de base de datos - `php bin/console doctrine:database:create`

Crear migracion - `php bin/console make:migration`

Ejecutar migraciones - `php bin/console doctrine:migrations:migrate`


## Form

Instalado de serie

## React

Habilitado con npm y en webpack.config.js

npm:
	- `npm install --save @babel/preset-react`
	- `npm install --save react react-dom prop-types babel-preset-react`
	Añade las características de ES6 en cualquier navegador
	- `npm install babel-polyfill babel-preset-env --dev`

webpack:
	- Linea ".enableReactPreset()"

Creamos un controlador (y vista) para react
`php bin/console make:controller ReactController`

Seguimos en [ejemplo de cloudways](https://www.cloudways.com/blog/symfony-react-using-webpack-encore/)

[Blog Jeffrey de testing y React](https://www.thinktocode.com/2018/06/14/symfony-unit-testing-with-a-database/)

[Blog jeffrey Routing react](https://www.thinktocode.com/2018/06/28/symfony-4-and-reactjs-routing/)

[Blog jeffrey Arquitectura de capas](https://www.thinktocode.com/2018/07/05/layered-architecture/)

### guia react estados

[blog](https://www.pensemosweb.com/react-metodos-ciclo-vida-componente/)

### router react

Instalar jsroutingbundle con - `composer require frindesofsymfony/jsroutingbundle --dev`

Habilitar el bundle en config\bundle.php

[docs symfony](https://symfony.com/doc/master/bundles/FOSJsRoutingBundle/installation.html)

