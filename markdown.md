# Markdown

[Pagina de Joe di Castro](http://joedicastro.com/pages/markdown.html)

## Salto de linea

Para realizar un salto de línea dentro del mismo párrafo, hay que dejar dos espacios en blaco despues del punto y aparte.
    
## Títulos

* # H1

* ## Esto es un H2

* ### Esto es un H3

* #### Esto es un H4

* ##### Esto es un H5

* ###### Esto es un H6


Esto es un H1
=============

Esto es un H2
-------------


## Formato

**Esto es negrita**


__Esto también es negrita__


*Esto es cursiva*

_Esto también es cursiva_


***Esto es negrita y cursiva***


___Esto también es negrita y cursiva___


Esto es una línea normal

> Esto es parte de un bloque de cita.
> Esto es parte del mismo bloque de cita.
>
> > Esto es otro bloque de cita anidado.
> > Esto es parte del bloque anidado.
>
> Esto es parte del bloque de cita de primer nivel.

## Listas

Una definición puede constar de varios párrafos.

Otro termino
Primer termino
 : Primera definición
 : Otra Def

	Segundo párrafo de Otra def definición

Segundo termino
 : Segunda definición


Se pueden mezclar distintos tipos de listas y anidar unas dentro de otras.

1. Esto es una lista ordenada
2. Segundo elemento de la lista ordenada
    1. Esta es una lista ordenada anidada dentro de otra
        * Lista desordenada anidada a tercer nivel
        * Segundo elemento de esta lista
    2. Este es el segundo elemento de la lista ordenada anidada

## Enlaces

[Con titulo](http://joedicastro.com "titulo")

[Sin titulo](http://joedicastro.com)

[Enlace 1][1], [Enlace 2][2], [Enlace 3][3]

 [1]: http://joedicastro.com/consejos
 [2]: http://joedicastro.com/consejos "Consejos"
 [3]: http://joedicastro.com/

## Tablas

| Elemento | Cantidad | Precio |
| :------- | :------: | -----: |
| Item 1   | 15       | 150€   |
| Item 2   | 3250     | 23,65€ |


## Código

    Esto es un párrafo de código.

~~~
Esto también es un párrafo de código.
~~~

Esto es un párrafo normal, con un trozo de código, `import this` insertado en el medio del mismo.


## Lineas

[Linea vacia]

***

[Linea vacia]
[Linea vacia]

---

[Linea vacia]
[Linea vacia]

 - - -

[Linea vacia]

## Notas

Esto es un texto con nota al pie [^nota1] y esta es otra nota [^nota2]

[^nota1]: Esto es una nota al pie de página.
[^nota2]: Esto es la segunda nota al pie.

## Abreviaturas

La especificación HTML es mantenida por el W3C Consortium.

  * [HTML]: Hyper Text Markup Language
  * [W3C Consortium]:  World Wide Web Consortium

## Identificadores de cabecera

### Esto es una cabecera 3 con un Id {#cabecera1}

[Enlace a esa cabecera](#cabecera1)

## Codigo fuente

    :::python
    import lifetime
    
    for each_day in lifetime.days():
        carpe_diem()

* apache
* bash y console
* css
* diff o udiff
* erlang
* go
* haskell
* html
* java
* js
* latex
* cl
* lua
* mysql
* pascal y delphu
* perl
* php
* python ó py ó pycon ó pytb ó python3 ó cython
* ruby
* scala
* scheme
* smalltalk
* sql
* sqlite3
* text
* vala
* vbnet
* vim
* xml




Leeme

Este es el resumen de Markdown y Dingus

Dos espacios para crear una nueva linea.  

Dingus
Programa escrito en Markdown  
    [Dingus](https://daringfireball.net/projects/markdown/dingus)

Syntax Cheatsheet:
Phrase Emphasis

*italic*   **bold**
_italic_   __bold__

Links

Inline:

An [example](http://url.com/ "Title")

Reference-style labels (titles are optional):

An [example][id]. Then, anywhere
else in the doc, define the link:

  [id]: http://example.com/  "Title"

Images

Inline (titles are optional):

![alt text](/path/img.jpg "Title")

Reference-style:

![alt text][id]

[id]: /url/to/img.jpg "Title"

Headers

Setext-style:

Header 1
========

Header 2
--------

atx-style (closing #'s are optional):

# Header 1 #

## Header 2 ##

### Header 3

###### Header 6

Lists

Ordered, without paragraphs:

1.  Foo
2.  Bar

Unordered, with paragraphs:

*   A list item.

    With multiple paragraphs.

*   Bar

You can nest them:

*   Abacus
    * answer
*   Bubbles
    1.  bunk
    2.  bupkis
        * BELITTLER
    3. burper
*   Cunning

Blockquotes

> Email-style angle brackets
> are used for blockquotes.

> > And, they can be nested.

> #### Headers in blockquotes
> 
> * You can quote a list.
> * Etc.

Code Spans

`<code>` spans are delimited
by backticks.

You can include literal backticks
like `` `this` ``.

Preformatted Code Blocks

Indent every line of a code block by at least 4 spaces or 1 tab.

This is a normal paragraph.

    This is a preformatted
    code block.

Horizontal Rules

Three or more dashes or asterisks:

---

* * *

- - - - 

Manual Line Breaks

End a line with two or more spaces:

Roses are red,   
Violets are blue.
