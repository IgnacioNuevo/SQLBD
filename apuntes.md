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
ROUND ( Expresion_Numerica , Nº_De_redondeo )
```
#### EJEMPLOS
| Ejemplos          |   Resultado    |
| ----------------- | :------------: |
| ROUND(748.58,  1) |   748.6        | 
| ROUND(748.58, -1) |   750          | 

###   LENGHT
Devuelve el numero de caracteres de una cadena

#### Sintaxis ROUND
```sql
LENGHT(cadena)
```
###   LEFT y RIGHT
Devuelven un número concreto de caracteres de una cadena.
* **LEFT** empieza a contar por la izquierda
* **RIGHT** empieza a contar por la derecha

#### Sintaxis LEFT y RIGHT
```sql
LEFT(cadena)
```

```sql
RIGHT(cadena)
```
###   ORDER BY
Con el **ORDER BY** podemos filtrar por el orden de las tuplas.
* Se puede ordenar por orden ASCENDENTE (**ASC**) o DESCENDENTE (**DESC**)
* Por defecto ordenará por orden ASCENDENTE.

#### Sintaxis ORDER BY
```sql
SELECT columna1, columna2,...
FROM nombre_tabla
ORDER BY columna1, columna2, ... ASC|DESC;
```
###   SUBCONSULTAS O CONSULTAS ANIDADAS
Son consultas completas que podemos poner por ejemplo dentro de una clausula **WHERE** y nos permiten hacer dos tablas independientes y comparar por tanto dos tuplas.

* Las subconsultas son independientes de la consulta por tanto no hace falta poner un alias a las columnas o tablas (Lo que pasa en las Vegas se queda en las Vegas 🎰♠♣♥♦🎰 )

####  EJEMPLO SUBCONSULTAS
```sql
SELECT name 
FROM world
  WHERE population > 
     (SELECT population 
      FROM world
      WHERE name='Russia');
```
###   CONCAT
Permite la concatenación o combinación de dos o más valores o cadenas.
* Se puede utilizar en el **SELECT** o dentro de un predicado.

#### Sintaxis CONCAT
```sql
CONCAT ( cadena_valor1, cadena_valor2 [, cadena_valorN ] ) ;
```
####  EJEMPLOS CONCAT
```sql
SELECT CONCAT ( 'Feliz ', 'Cumpleaños ', 11, '/', '25' ) AS Result;
```
  El resultado sería una columna con nombre Feliz Cumpleaños 11/25

```sql
SELECT name, CONCAT(ROUND(population/(SELECT population
                               FROM world
                               WHERE name ='Germany')*100,0),'%')
FROM world;
```
  En este caso la consulta concatena el **%** al porcentaje de población de cada país respecto a la población de \"Alemania\".
    Es decir dividimos la población de cada país entre la de alemania y la multiplicamos por 100 para saber el porcentaje, lo ponemos dentro de un **ROUND** para redondear sin decimales y todo el conjunto dentro de un **CONCAT** para añadirle el porcentaje a continuación del resultado.

###   ALL
El operador **ALL** se utiliza en predicados.
* Permite comparar un registro con todos los registros de una subconsulta con un comparador antes del **ALL**

#### Sintaxis ALL
```sql
SELECT nombre_columna(s)
FROM nombre_tabla
WHERE nombre_columna comparador ALL
                                (SELECT nombre_columna
                                FROM nombre_tabla
                                WHERE condición);
```
####  EJEMPLO ALL
```sql
SELECT name
FROM world
WHERE gdp >= ALL(SELECT gdp
                 FROM world
                 WHERE continent = 'Europe' AND gdp > 0)
```

* Es Importante fijarse en la diferencia entre el > y >=, porque debido a esto en las consultas no nos mostraría como resultado el país de **'EUROPE'** con mayor gdp debido a que en este caso Alemania no es mayor que Alemania, por tanto sería necesario el comparador >=.

###   FUNCIONES SUM, COUNT Y AVG
* La función **SUM**  nos devuelve la suma de los valores numéricos de las tuplas de una columna.
* La función **COUNT** nos devuelve una tupla con el número de tuplas que tiene una columna.
* La función **AVG** realiza la media de los valores numéricos de las tuplas de una columna.

#### Sintaxis SUM
```sql
SELECT SUM(columna1)
FROM nombre_tabla
WHERE condición;
```
#### Sintaxis COUNT
```sql
SELECT COUNT(columna1)
FROM nombre_tabla
WHERE condición;
```
#### Sintaxis AVG
```sql
SELECT AVG(columna1)
FROM nombre_tabla
WHERE condición;
```
###   DISTINCT
El distinct permite evitar duplicados, es decir en caso de haber más de un registro con un mismo valor lo devuelve una sola vez

#### Sintaxis DISTINCT
```sql
SELECT DISTINCT columna1, columna2, ...
FROM nombre_tabla;
```
###   GROUP BY
**GROUP BY** permite agrupar por tuplas. Es decir por si hacemos un **GROUP BY** de una columna agrupará en base a cada tupla de esa columna.
* Normalmente el **GROUP BY** se utiliza junto a funciones agregadas (SUM,COUNT,AVG, MIN y MAX) lo cual permite filtrar los resultados de una función agrupados en cada una de las tuplas de la columna sobre la que hacemos el **GROUP BY**.

#### Sintaxis GROUP BY
```sql
SELECT nombre_columna(s)
FROM nombre_tabla
WHERE condición
GROUP BY nombre_columna(s);
```
####  EJEMPLO GROUP BY
![GROUP BY](C:/Users/Ignacio/Desktop/CapturaBD.png)

