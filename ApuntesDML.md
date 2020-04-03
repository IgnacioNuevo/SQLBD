- [Apuntes DML](#Apuntes-DML)
  - [INSERT](#INSERT)
  - [UPDATE](#UPDATE)
  - [DELETE](#DELETE)
# Apuntes DML
DML es un sublenguaje de SQL que permite introducir datos y modificar datos en las tablas de las bases de datos.

Las tres sentencia de DML son:
* **INSERT** permite insertar los valores en una base de datos.
* **UPDATE** permite actualizar y modificar los valores de los registros.
* **DELETE** permite eliminar los registros de una tabla.

## INSERT
Sintaxis:

```sql
INSERT INTO <nombre-de-la-tabla>
[(<atributo1>,<atributo2>,...)]
VALUES 
      (<valor1A>,valor2A,...),
      (<valor1B>,<valor2B>,...)
```
Ejemplos:

```sql
INSERT INTO world
(name, continent, area)
VALUES 
      ('Spain', 'Europe', '100'),
      ('Portugal', 'Europe', '100');
```
En este caso añadimos los registros Spain y Portugal a la columna name, Europe a la columna continent y 100 a la columna area.

```sql
INSERT INTO world
(name, continent, area)
SELECT nombre, continente, área
FROM mundo
WHERE continente='Europa';
```
En este otro ejemplo lo que hacemos es añadir los registros nombre, continente y área de la tabla mundo y que su continente sea Europa en los registros name, continent y area de la tabla world. Es decir añadimos los registros de otra tabla que ya tiene registros mediante el **SELECT**

## UPDATE
Sintaxis:

```sql
UPDATE <nombre-de-la-tabla>
SET <atributo1> = <valor1>
    <atributo2> = <valor2>
[WHERE <predicado>]
```
Ejemplo:

```sql
UPDATE world
SET continent = 'Africa'
WHERE name='Spain'
OR name ='Portugal';
```

## DELETE
Sintaxis:

Sintaxis:

```sql
DELETE FROM <nombre-de-la-tabla>
[WHERE <predicado>]
```

Ejemplo:

```sql
DELETE FROM world
WHERE continent = 'Europe'
```

