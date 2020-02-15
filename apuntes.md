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
* El operador **IN** permite especificar múltiples valores en un predicado.
* El **IN** es equivalente a poner varios valores entre operadores **OR**

#### Sintaxis IN
```sql
SELECT columna1, columna2,columna3 AS departamento ...
FROM nombre_tabla
WHERE nombre_columna 
  IN(valor1,valor2,...);
```
###  BETWEEN
* El operador **BETWEEN** permite especificar rangos de valores (puedes ser números, texto o datos).
* Si le ponemos un **NOT** delante excluiría el rango es decir mostraría todos los valores que no estuvieran dentro del rango del **BETWEEN**
#### Sintaxis BETWEEN
```sql
SELECT columna1, columna2,columna3 AS departamento ...
FROM nombre_tabla
WHERE nombre_columna BETWEEN valor1 AND valor2;
  ```
###  COMPARADORES
| Símbolo | Significado      |
| ------- | :---------------:|
| =       | Igual a          | 
| >       | Mayor que        | 
| <       | Menor que        | 
| >=      | Mayor o igual que|
| <=      | Menor o igual que|
| <>      | No es igual a    |

### COMODINES

| Símbolo | Significado                                                  |
| :-----: | ------------------------------------------------------------ |
| %       | Sustituye 0 o más caracteres                                 | 
| _       | Sustituye un único caracter                                  | 
| []      | Permite sustituir por los caracteres dentro de los corchetes | 
| -       | Permite un rango de caracteres dentro de los corchetes       |
| ^       | Excluye los caracteres dentro de los corchetes               |

###  LIKE
El operador **LIKE** se puede utilizar en la clausula **WHERE** y permite buscar un patrón.
* A diferencia del **=** el cual compara con una cadena exactamente igual, el **LIKE** permite incluir comodines.
    
    Permite los comodines:
    * %
    * _

#### Sintaxis LIKE
```sql
SELECT columna1, columna2,columna3 AS departamento ...
FROM nombre_tabla
WHERE nombre_columna LIKE patron;
  ```
###  ROUND 
Es un operador que permite redondear un valor numérico a la longitud especificada 

#### Sintaxis ROUND
```sql
ROUND ( numeric_expression , length )
```
#### EJEMPLOS
| Ejemplos          |   Resultado    |
| ----------------- | :------------: |
| ROUND(748.58,  1) |   748.6        | 
| ROUND(748.58, -1) |   750          | 

###   LENGHT
