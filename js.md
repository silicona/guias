# JavaScript

## Backbone

[Docs Backbone](https://backbonejs.org/#Events-catalog)

[Docs Backbone Interior](https://backbonejs.org/docs/backbone.html)

[explicacion bind](https://blog.bigbinary.com/2011/08/18/understanding-bind-and-bindall-in-backbone.html)

[Super en Backbone](http://js.dokry.com/super-en-backbone.html)



### Eventos

Los eventos se propagan a su padre inmediato.

`_.bindAll(this, 'funcion')` - Aplica el contexto this a la función (en string)

`this.listenTo(model, 'evento', funcion)` - This escucha el evento lanzado por modelo y ejecuta la función con this como contexto.


## DataTables

[web de referencia](https://datatables.net/reference/option/pagingType)

### Responsive

Al hacer responsive, se eliminan las columnas sobrantes y se guardan en una fila child. Se pierden los atributos de la columna.

## Select2

`$(.select2).val(1).trigger('change');` - aplicar un valor al select y disparar change para que se actualice select2.