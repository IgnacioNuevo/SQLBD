# Apuntes bases de datos

## Sentencias SQL/DQL

### SELECT y FROM

* El **SELECT** nos permite seleccionar las columnas que queremos mostrar en la consulta

EL **\***  nos permite mostrar por pantalla todas las columnas

Con el **AS** cambiamos el nombre de la columna cuando mostramos los datos.

* El **FROM** indica la tabla de la que seleccionamos los datos


```sql
SELECT columna1, columna2,columna3 AS departamento ...
FROM nombre_tabla;
```
### WHERE
* El **WHERE** sirve para filtrar por tuplas. En el escribimos un predicado
```sql
SELECT columna1, columna2,columna3 AS departamento ...
FROM nombre_tabla
WHERE condición;
```
###  OPERADORES AND, OR y NOT
Estos operadores se pueden utilizar por ejemplo en la clausula WHERE.

* El **AND** sirve para filtrar con más de una condición y ambas condiciones situadas entre el AND se deben cumplir.
* El **OR** sirve para filtrar con más de una condición y al menos una de las dos situadas entre el operador se debe cumplir.
* El **NOT** muestra el registro si la condición no es correcta. 

#### Sintaxis AND
```sql
SELECT columna1, columna2,columna3 AS departamento ...
FROM nombre_tabla
WHERE condicion1 AND condicion2 AND condicion3 ...;
```
#### Sintaxis OR
```sql
SELECT columna1, columna2,columna3 AS departamento ...
FROM nombre_tabla
WHERE condicion1 OR condicion2 OR condicion3 ...;
```


#### Sintaxis NOT
```sql
SELECT columna1, columna2,columna3 AS departamento ...
FROM nombre_tabla
WHERE NOT condición;
```

###  IN
