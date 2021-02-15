# Docker

[Docs](https://docs.docker.com/docker-for-mac/)

Utilizado para montar SQLSERVER de microsoft en Mac


[comandos](https://docs.docker.com/engine/reference/commandline/stop/)

## Comandos útiles

`docker ps -a` - Muestra los contenedores activos y pasivos

`docker stop nombre_contenedor` - detiene el contenedor

## SQLSERVER

[SqlServer para Docker](https://hub.docker.com/_/microsoft-mssql-server)
[Blog de conexion](https://dockertips.com/ms_sql_server)
[docs microsoft](https://docs.microsoft.com/en-us/sql/azure-data-studio/quickstart-sql-server?view=sql-server-2017)

Iniciar SqlServer en docker
`docker run -e "ACCEPT_EULA=Y" -e "SA_PASSWORD=Pa$$word" -p 1433:1433 -d microsoft/mssql-server-linux:2017-latest`

`--name nombre_docker` - Asigna un nombre al docker al iniciarlo

Conexión a la BBDD
`docker exec -it <nombre_contenedor> /opt/mssql-tools/bin/sqlcmd -S localhost -U sa -P Pa$$word`

Crear base de datos
[blog](https://database.guide/create-a-sql-server-database-with-azure-data-studio/)

Docs de SQL Server
[Docs](https://www.sqlservertutorial.net/sql-server-basics/sql-server-foreign-key/)

### Comprobar la version
1> `select @@version`
2> `go`

Se obtiene la version de Microsoft SQL Server

### Conexion con Azure

Iniciar docker y hacer run de la imagen

Abrir Azure Data Studio y conectar con:
  localhost,1433
  sa
  tu_password




