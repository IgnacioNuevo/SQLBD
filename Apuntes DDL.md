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

### DROP
