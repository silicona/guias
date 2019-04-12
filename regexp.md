# RegExp

## Sintaxis de Exp Reg

[Cheatsheet](cheat-regexp.pdf)

## Sublime Text

### Expresión multilinea

Ejemplo a captar:

***

`<IfModule mod_setenvif.c>
    <IfModule mod_headers.c>
        <FilesMatch "\.(bmp|cur|gif|ico|jpe?g|png|svgz?|webp)$">
            SetEnvIf Origin ":" IS_CORS
            Header set Access-Control-Allow-Origin "*" env=IS_CORS
        </FilesMatch>
    </IfModule>
</IfModule>`

***

Expresión que la capta:

	(<IfModule.*((?!</IfModule>\n\n).|\n)+</IfModule>)

Sustitución con comillas para convertirlo en código md:

	`$1`


Expresion para solo un IfModule:

	(<IfModule.*((?!</IfModule>).|\n)+</IfModule>)

## Lookahead
La regexp observa lo que sigue del grupo a capturar:
  : Positiva - `/q(?=u)/` sobre quit captura 'q'
  : Negativa - `/q(?!u)/` sobre quit NO captura 'q'

## Lookbehind
La regexp observa lo que antecede al grupo a capturar:
  : Positiva - `/(?<=a)b/`sobre cab captura 'b'
  : Negativa - `/(?<!a)b/` sobre cab NO captura 'b'
