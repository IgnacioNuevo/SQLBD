# MariaDB

## Ejercicio 1


![1](img/Capturas/1.PNG)

Una vez iniciamos MariaDB el primer paso será crear una base de datos como vemos en la captura, después utilizamos el comando use para modificar la base de datos.


![2](img/Capturas/2.PNG)

En este caso no podemos crear dominios ya que MariaDB no lo permite


![3](img/Capturas/3.PNG)

Empezaremos a crear las diferentes tablas con CREATE.
Podemos ver las tablas creadas con **show tables** y la estructura con **DESCRIBE**.


![4](img/Capturas/4.PNG)



![6](img/Capturas/6.PNG)




![7](img/Capturas/7.PNG)




![9](img/Capturas/9.PNG)


Separando con **;** podemos separar los diferentes **DESCRIBE** para ver la estructura de todas las columnas que enumeremos.



![10](img/Capturas/10.PNG)



## Ejercicio 2

Ahora creamos otra base de datos y sus respectivas tablas.
![10](img/Capturas/11ejercicio2.PNG)



![10](img/Capturas/12.PNG)


![10](img/Capturas/13.PNG)


![10](img/Capturas/14.PNG)

## Comandos

Los tres comandos básicos para ver la estructura de una base de datos son:

* **SHOW DATABASE**, permite ver las bases de datos.
* **SHOW TABLES**, permite ver las tablas de una base de datos.
* **SHOW COLUMNS**, permite ver la estructura las columnas de una tabla.

###  Ejemplos
![10](img/Capturas/show.PNG)

En esta imagen podemos ver los tres comandos mencionados anteriormente junto a su sintaxis y resultado obtenido. En este caso con el comando **SHOW COLUMNS** hemos utilizado la opción **full** que muestra a mayores los campos **EXTRA** **PERMISOS** Y **COMENTARIOS**.

![10](img/Capturas/describe.PNG)
Para ver la estructura de una tabla podemos utilizar también **DESCRIBE** sin embargo al utilizar clausulas como el **LIKE** o el **WHERE** para filtrar puede resultar mas sencillo utilizar el comando **SHOW COLUMNS**.

![10](img/Capturas/insert.PNG)

Añadimos datos de prueba a una tabla para consultarlos después.

![10](img/Capturas/select.PNG)
  

Hacemos un select y podemos comprobar los datos de la tabla.