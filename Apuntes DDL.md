# Apuntes DDL

DDL es un sublenguaje de SQL que nos permite definir las estructuras que almacenaran los datos de la base de datos.

## SENTENCIAS

* **CREATE**, permite crear la base datos, tablas, vistas, etc.

* **ALTER** permite modificar la estructura de una tabla.

* **DROP** permite eliminar una estructura, es decir una tabla, la base de datos, etc.

###  CREATE
La sintaxis para crear una base de datos es la siguiente:
```sql
CREATE (DATABASE|SCHEMA)
[IF NOT EXIST] nameDB
[CHARACTER SET CharsetName]
```
* Podemos utilizar tanto **DATABASE** como **SCHEMA** como sinónimos
* **IF NOT EXIST** es opcional y se utiliza para que en caso de ya existir la tabla no crearla.
* EL **CHARSET SET** también es opcional y nos permite cambiar el tipo de caracteres admitidos.
La sintaxis para crear una tabla es la siguiente
```sql
CREATE TABLE "nombre_tabla"
("columna 1" "tipo_de_datos_para_columna_1",
"columna 2" "tipo_de_datos_para_columna_2",
... );
```

### ALTER
La sintaxis de **ALTER** para añadir o eliminar columnas es la siguiente:
```sql
ALTER TABLE table_name
ADD column_name datatype,
DROP column_name [CASCADE|RESTRICT];
```
* Con **ADD** añadimos columnas y con **DROP** las eliminamos, también es necesario indicar el tipo de dato.
* Al eliminar la columna podemos eliminarla en cascada, es decir eliminara todas las estructuras que dependan de la columna, con restrict  no eliminaremos la columna si existe una o mas estructura que dependan de ella.

También podemos utilizar **ALTER** para modificar una columna:
```sql
ALTER TABLE table_name
ALTER COLUMN column_name datatype;
```
### DROP
De igual manera que con **CREATE** y **DROP** podemos eliminar tanto la base de datos como una tabla.

Para eliminar la base de datos la sintaxis es:
```sql
DROP SCHEMA
[IF EXISTS] <Nombre-de-la-base-de-datos>
[CASCADE|RESTRICT];
```
* **CASCADE** borra la base de datos aunque tenga datos
* **RESTRICT** protege la base datos si no está vacía.

Para eliminar una tabla:
```sql
DROP TABLE
[IF EXISTS] <Nombre-de-la-tabla>
[CASCADE|RESTRICT];
```


