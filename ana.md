# mysql

- Para acceder por consola, ejecutar mysql directamente, el directorio de origen es indiferente. En el caso de que de acceso denegado ejecutar sudo mysql.
- En mysql siempre terminar la orden con ;
- Cuando intentamos entrar en nuestra base de mysql puede que no nos permita por cuestión de permisos (access denied). Podemos solventarlo entrando con el superusuario (sudo mysql) o cambiar los permisos de nuestro user.
- Para ver todas las bases de datos ejecutamos `show databases;`

## comandos

- wild card: * (comodín) - con el asterisco se seleccionan todos los campos de una tabla
- Seleccionar campos de una tabla donde el campo tenga este valor: select * from [tabla] where [nombre de campo]=[valor]
- Orden para seleccionar datos de una tabla: select * from [nombre de tabla];
- Orden para seleccionar campos concretos: select [nombre campo] , [nombre campo];
- Orden para seleccionar registro concreto: select * from [tabla] where [campo]=[valor];
- Orden para seleccionar todo con varias campos con un valor: `select * from clientes where credito=1500 and nsucursal >1008;`
- Orden para seleccionar todo con varias campos con un valor: `select * from clientes where nombre="pepe" and apellidos="marin";`
- Comando para insertar registro: `insert into [tabla con comillas simple](campo1, campo2, campo3) values(valor1, valor2, valor3);`

- Orden para examinar la estructura de la tabla: `describe [tabla];`


*** NUNCA OLVIDAR EL SEGMENTO WHERE PORQUE MODIFICA TODA LA TABLA Y LO MISMO SI UTILIZAMOS LA ORDEN DELETE QUE BORRARÁ TODA LA TABLA

- Orden para modificar un campo: update ["tabla" con comillas] set [campo]=[valor] where [campo]=[valor];

## Tipos de datos

- Enteros:  números (van sin comillas)
- Strings: caracteres alfanuméricos (con comillas) varchar o char
- Fechas:  Formato mysql- aaaa-mm-dd (hay que poner todos los caracteres, completando con 0): 2014-04-02
		 	Formato fecha y hora: aaaa-mm-dd:hh:mm:ss
- NULL: 	Dato nulo (distinto de string vacío)



