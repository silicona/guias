# htaccess

[Weblantropia](https://www.weblantropia.com/2016/07/28/enrutamiento-urls-htaccess-php/)

[WebEmpresa 10 consejos](https://www.webempresa.com/blog/10-sencillos-consejos-reforzar-seguridad-wordpress-usando-htaccess.html)

[AyudaWP](https://ayudawp.com/todo-sobre-htaccess/)

[Directivas utiles](http://tinoarauz.blogspot.com.es/2009/05/comandos-y-directivas-htaccess.html) - Hay que revisar.

[Flags](https://httpd.apache.org/docs/2.4/rewrite/flags.html)

[Sheet mod_rewrite](https://www.cheatography.com/davechild/cheat-sheets/mod-rewrite/)

## Mod_write check
Create an htaccess file in the document root and add the following rewriteRule :

`RewriteEngine on`
`RewriteRule ^helloWorld/?$ /index.php [NC,L]`

Now visit `http://example.com/HelloWorld` , You will be internally forwarded to /index.php page of your site. Otherwise, if mod-rewrite is disabled , you will get a 500 Internel server error. 

- Reescribe si el archivo no existe: `RewriteCond %{REQUEST_FILENAME} !-f`
- Reescribe si el directorio no existe: `RewriteCond %{REQUEST_FILENAME} !-d`

-	Reescribe si el Método HTTP es TRACE  o TRACK: `RewriteCond %{REQUEST_METHOD} ^(TRACE|TRACK)`
-	Reescribe todo con 403 Forbidden (inmediatamente debajo de un RewriteCond): `RewriteRule .* - [F]`

- Reescribe si Referer es empty: `RewriteCond %{HTTP_REFERER} !^$`
- Reescribe si Referer no es tu_dominio.com (util para evitar hotlinkg): `RewriteCond %{HTTP_REFERER} !^http://(www.)?tu_dominio.com/.*$ [NC]`
- Reescribe la url a imagen preparada para hotlinking: `RewriteRule .(gif|jpg)$ http://www.tu_dominio.com/hotlink.gif [R,L]`

### Security

- Negar el acceso a un archivo o carpeta
```
<files wp-config.php>
	order allow,deny
	deny from all
	</files>
```

### FLAGS

| Flag | Significado |
|:-----|:------------|
| **mod_re­write Rewrit­eRule Flags**	|
|	C 		| Chained with next rule |
| CO (cookie) | Set specified cookie |
| E (var:­value) | Set enviro­nmental variable “var” to “value” |
| F | Forbidden (403 header) |
| G | Gone - no longer exists |
| H (handler) | Set handler |
| L | Last - stop processing rules |
| N | Next - continue processing |
| NC | Case insens­itive |
| NE | Do not escape output |
| NS | Ignore if subrequest |
| P | Proxy |
| PT | Pass through |
| R (code) | Redirect to new URL, with optional code (see below) |
| QSA | Append query string |
| S (x) | Skip next x rules |
|T (mime­-type) | Set mime type |
| **mod_re­write Rewrit­eCond Flags** |
| NC | Case insens­itive |
| OR | Combine with next rule using 'OR' instead of the default of 'AND' |

