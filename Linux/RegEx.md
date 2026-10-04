
|     | **Operadores** | **Descripción**                                                                                                                                                                |
| --- | -------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| 1   | `(a)`          | Los paréntesis redondos se utilizan para agrupar partes de una regex. Dentro de los paréntesis, puedes definir patrones adicionales que deben procesarse juntos.               |
| 2   | `[a-z]`        | Los corchetes se utilizan para definir clases de caracteres. Dentro de los corchetes, puedes especificar una lista de caracteres a buscar.                                     |
| 3   | `{1,10}`       | Las llaves se utilizan para definir cuantificadores. Dentro de las llaves, puedes especificar un número o un rango que indica cuántas veces debe repetirse un patrón anterior. |
| 4   | `\|`           | También llamado operador OR, muestra resultados cuando una de las dos expresiones coincide.                                                                                    |
| 5   | `.*`           | Funciona de manera similar a un operador AND, mostrando resultados solo cuando ambas expresiones están presentes y coinciden en el orden especificado.                         |
Supongamos que usamos el operador `OR`. La regex busca uno de los parámetros de búsqueda dados. En el siguiente ejemplo, buscamos líneas que contengan la palabra `my` o `false`. Para usar estos operadores, necesitas aplicar la regex extendida usando la opción `-E` en grep.

#### Operador OR
`$ grep -E "(my|false)" /etc/passwd  lxd:x:105:65534::/var/lib/lxd/:/bin/false pollinate:x:109:1::/var/cache/pollinate:/bin/false mysql:x:116:120:MySQL Server,,:/nonexistent:/bin/false$`

Dado que uno de los dos parámetros de búsqueda siempre aparece en las tres líneas, las tres líneas se muestran en consecuencia. Sin embargo, si usamos el operador `AND`, obtendremos un resultado diferente para los mismos parámetros de búsqueda.

#### Operador AND

`$ grep -E "(my.*false)" /etc/passwd  mysql:x:116:120:MySQL Server,,:/nonexistent:/bin/false`

Básicamente, lo que estamos diciendo con este comando es que estamos buscando una línea en la que queremos ver tanto `my` como `false`. Un ejemplo simplificado también sería usar `grep` dos veces, que se vería así:


`$ grep -E "my" /etc/passwd | grep -E "false"  mysql:x:116:120:MySQL Server,,:/nonexistent:/bin/false`