# Netbeans - Sobre Java

## Atajos (+tab)

sout - System.out.println("")
psv [8.0] - public static void main(String[] args)
main [12.0] - public static void main(String[] args)

Ctrl + espaciadora - Al final de una clase, sugiere los paquetes de instalacion para importarlo en el script

## Tomcat

Añadir la carpeta de Tomcat como servidor de Netbeans.

### Errores

java.net.BindException: Address already in use
[Doc blog](https://www.baeldung.com/tomcat-bind-exception)

  * Mac: Encontrar el proceso y destruirlo = `lsof -t -i :[puerto]` y `kill -9 -[puerto]`

