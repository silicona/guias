# Spring sobre Eclipse

[Curso Youtube Pildoras Informaticas](https://www.youtube.com/watch?v=kFIvslQQZ9k&list=PLU8oAlHdN5Blq85GIxtKjIXdfHPksV_Hm&index=1)

Necesaria vista de Eclipse de Java, no JavaEE:
  - En menu window - Perspective - Open Prespective - Java
  - Iconos de Perspectiva a la derecha de la pantalla - Java

Archivos jar de Spring:
  - [Url de descarga](https://repo.spring.io/release/org/springframework/spring/)
  - Descargar la carpeta dist de la version deseada

Importar las librerias sping al nuevo proyecto Java:
  - Crear carpeta libs en el raiz
  - Copiar y pegar todos los archivos de la carpeta libs .jar de Spring
  - Insertar el build path: Properties - JavaBuildPath - Libraries - ClassPath (si hay distinción con ModulePath) - Add JAR y seleccionar todos los archivos de la carpeta lib del raiz

Archivo de configuración:
  - xml (antiguo) - Creación en Video 8
  - Java Source code
  - Java Annotations

## Creacion de xml - manual

Crear nuevo archivo en raiz (applicationContext.xml).

Codigo a pegar en el archivo:

	<?xml version="1.0" encoding="UTF-8"?>
	<beans xmlns="http://www.springframework.org/schema/beans"
		xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
		xmlns:context="http://www.springframework.org/schema/context"
		xsi:schemaLocation="
		http://www.springframework.org/schema/beans
		http://www.springframework.org/schema/beans/spring-beans-3.1.xsd
		http://www.springframework.org/schema/context
		http://www.springframework.org/schema/context/spring-context-3.1.xsd
		">
	</beans>

Se crean los bean necesarios en el xml
