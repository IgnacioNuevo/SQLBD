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
* Al eliminar la columna podemos eliminarla en cascada (**CASCADE**), es decir eliminara todas las estructuras que dependan de la columna, con **restrict**  no eliminaremos la columna si existe una o mas estructura que dependan de ella.

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

## CONSTRAINTS
Un constraint es una restriccion que permite limitar el tipo de dato que puede ingresarse en una tabla. 

Se pueden utilizar con la instrucción **CREATE TABLE** y con **ALTER TABLE**

Tipos de **constraints**:

* **PRIMARY KEY**
* **FOREIGN KEY**
* **NOT NULL**
* **UNIQUE**
* **CHECK**

### PRIMARY KEY

La sintaxis es la siguiente:
```sql
[CONSTRAINT <nombre-de-la-restricción>]
PRIMARY KEY (<atributo>);
```
* **CONSTRAINT** es opcional y sirve para darle un nombre al constraint.
* Dentro de **PRIMARY KEY** por mas de un atributo por tanto podemos poner mas de un atributo dentro del paréntesis separados por comas.
* También se puede utilizar el constraint **PRIMARY KEY** colocándolo simplemente detrás del atributo que va a ser clave principal como en el siguiente ejemplo:
```sql
CREATE TABLE Sede (
  Nome_Sede CHAR(10) PRIMARY KEY,
  Campus CHAR(10),
);
```
* Sin embargo esto **solo lo podemos hacer si la clave principal está formada por un solo atributo**, es decir si está formada por dos atributos tendremos que hacerlo de la forma anterior.

### FOREIGN KEY
Sintaxis:
```sql
[CONSTRAINT <nombre-de-la-restricción>]
FOREIGN KEY (<atributo>)
REFERENCES <nombre-de-la-tabla-referenciada>[(atributos-referenciados)]
[ON DELETE CASCADE|NO ACTION|SET NULL|SET DEFAULT]
[ON CASCADE CASCADE|NO ACTION|SET NULL|SET DEFAULT];
```
Añadimos la FK a un atributo y con **REFERENCES** seleccionamos la tabla de la que viene la clave ajena, opcionalmente podemos indicar el nombre del atributo en la otra tabla en caso de llamarse de forma diferente, en caso de no indicarlo seleccionara la clave principal de la otra tabla.
* **ON DELETE** especifica que hacer cuando los datos principales son borrados.
* **ON UPDATE** especifica que hacer cuando los datos principales son actualizados o modificados
* **CASCADE** los datos se eliminan o actualizan si se modifican en la tabla de la que proviene.
* **NO ACTION** los datos no se eliminan ni modifican si se modifican en la tabla de la que proviene. **Es la opción por defecto si no lo especificamos**.
* **SET NULL** si los datos de la tabla origen son modificados o eliminados se establecen en NULL.
* **SET DEFAULT** si los datos de la tabla origen son modificados o eliminados los datos tomaran los valores predeterminados. Esta opción no es muy utiliza. **OJO por defecto el valor predeterminado es NULL si no especificamos ningún valor predeterminado**.

### NOT NULL
Sirve para que las columnas no acepten valores nulos.

Ejemplo:
```sql
CREATE TABLE Departamento (
  Nome_Departamento CHAR(10) PRIMARY KEY,
  Teléfono CHAR(9) NOT NULL,
;
```
### UNIQUE
Permite agregar a una columna unicidad es decir que no se pueda repetir

Ejemplo:

```sql
CREATE TABLE Departamento (
  Nome_Departamento CHAR(10) NOT NULL UNIQUE,
  Teléfono CHAR(9) NOT NULL;
```
También se puede añadir en un CONSTRAINT:
```sql
CONSTRAINT UQ UNIQUE (Nome_Departamento,Teléfono);
```
* Cuando utilizamos el constraint de **PRIMARY KEY** este atributo es como si fuera **UNIQUE** + **NOT NULL**.

### CHECK
Sirve para limitar el valor que pueden ser utilizados en una columna o en una tabla.

Ejemplos:
```sql
CONSTRAINT CHECK-objetivo-positivo
CHECK objetivo >0
```
```sql
CONSTRAINT CHECK-SUELDO-MÁXIMO-DEPT-A
CHECK sueldo >= (
  SELECT sueldo
  FROM empleado
  WHERE dept ='A');
```

### TIPOS DE DATOS
| tipo de datos|   Descripción                                  |
| -------------| ---------------------------------------------- |
| **NUMEROS**  |   Descripción                                  |
| INTEGER      |   número entero                                |
| DECIMAL      |   número preciso                               |
| REAL         |   número no preciso                            |
| **TEXTO**    |   Descripción                                  |
| CHAR         |   texto de longitud fija                       |
| VARCHAR      |   texto de longitud variable                   |
| TEXT         |   texto de longitud ilimitada                  |
| **FECHAS**   |   Descripción                                  |
| DATE         |   día, mes, año                                |
| TIME         |   hora, minuto, segundo [zona horaria]         |
| TIMESTAMP    |   DATE+TIME                                    |

      
| BOOLEAN      | Valores   |
| -------------| --------- |
| TRUE    | verdadero |
| FALSE   | falso     |
| NULL    | nulo      |

| OTROS |
| ----- |
| MONEY |
| UUID  |
| JSON  |
| XML   |
| CIDR  |
| INET  |

### CREACIÓN DE DOMINIOS
