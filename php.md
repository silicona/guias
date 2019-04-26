# PHP

## SimpleXML

[Tutorial simple](https://diego.com.es/tutorial-de-simplexml)

### Detectar elementos repetidos en array

`
$repeated = array_filter(array_count_values($array_numerico), function($count) {
    return $count > 1;
});
foreach ($repeated as $key => $value) {
    echo "Clave '$key' está repetido $value veces<br />";
}
`