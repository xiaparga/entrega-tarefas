# Índice

- [MySQL](#mysql)
  - [Instalación y configuración de MySQL](#instalacion-y-configuracion-de-mysql)
    - [Servidor dedicado](#servidor-compartido)
    - [Servidor compartido](#servidor-compartido)
  - [Creación de bases de datos en MySQL](#creacion-de-bases-de-datos-en-mysql)
    - [Creación de base de datos a mano](#creacion-de-base-de-datos-a-mano)
    - [Creación de base de datos importando un archivo](#creacion-de-base-de-datos-importando-un-archivo)
  - [Estructura de una base de datos en MySQL](#muestra-de-estructura-y-de-datos-de-una-base-de-datos-en-mysql)

## Creación de Bases de Datos en MySQL <a name="creacion-de-bases-de-datos-en-mysql"></a>

Para crear una base de datos en MySQL, podemos crear a mano una base de datos poniendo operaciones de una en una o importar un archivo `.sql`.

Para el primer ejercicio, vamos a hacer de la 1ª forma.

### Creación de base de datos a mano <a name="creacion-de-base-de-datos-a-mano"></a>

![Creación-de-Bases-de-Datos-(1)](./img/Creación-de-Bases-de-Datos/A-mano/A-mano-(1).png)

Introducimos `sudo mysql -u root -p` y la contraseña del usuario **root** para empezar a crear la base de datos con sus tablas.

![Creación-de-Bases-de-Datos-(2)](./img/Creación-de-Bases-de-Datos/A-mano/A-mano-(2).png)

Introducimos `CREATE SCHEMA Investigacion;` para crear la base de datos 'Investigacion'.

![Creación-de-Bases-de-Datos-(3)](./img/Creación-de-Bases-de-Datos/A-mano/A-mano-(3).png)

Introducimos `USE Investigacion;` para poder usar la base de datos 'Investigacion' y crear las tablas dentro de ella.

![Creación-de-Bases-de-Datos-(4)](./img/Creación-de-Bases-de-Datos/A-mano/A-mano-(4).png)

Creamos la tabla `Sede` con sus tuplas.

![Creación-de-Bases-de-Datos-(5)](./img/Creación-de-Bases-de-Datos/A-mano/A-mano-(5).png)

Creamos la tabla `Departamento` con sus tuplas.

![Creación-de-Bases-de-Datos-(6)](./img/Creación-de-Bases-de-Datos/A-mano/A-mano-(6).png)

Creamos la tabla `Ubicacion` con sus tuplas.

![Creación-de-Bases-de-Datos-(7)](./img/Creación-de-Bases-de-Datos/A-mano/A-mano-(7).png)

Creamos la tabla `Grupo` con sus tuplas.

![Creación-de-Bases-de-Datos-(8)](./img/Creación-de-Bases-de-Datos/A-mano/A-mano-(8).png)

Creamos la tabla `Profesor` con sus tuplas.

![Creación-de-Bases-de-Datos-(9)](./img/Creación-de-Bases-de-Datos/A-mano/A-mano-(9).png)

Creamos la tabla `Proyecto` con sus tuplas.

![Creación-de-Bases-de-Datos-(10)](./img/Creación-de-Bases-de-Datos/A-mano/A-mano-(10).png)

Creamos la tabla `Participa` con sus tuplas.

![Creación-de-Bases-de-Datos-(11)](./img/Creación-de-Bases-de-Datos/A-mano/A-mano-(11).png)

Creamos la tabla `Programa` con sus tuplas.

![Creación-de-Bases-de-Datos-(12)](./img/Creación-de-Bases-de-Datos/A-mano/A-mano-(12).png)

Creamos la tabla `Financia` con sus tuplas.

![Modificación-de-Bases-de-Datos-(1)](./img/Creación-de-Bases-de-Datos/Modificación-de-Bases-de-Datos/Modificación-de-Bases-de-Datos-(1).png)

Modificamos la tabla `Departamento` añadiendo restricciones.

![Modificación-de-Bases-de-Datos-(2)](./img/Creación-de-Bases-de-Datos/Modificación-de-Bases-de-Datos/Modificación-de-Bases-de-Datos-(2).png)

Modificamos la tabla `Ubicacion` añadiendo restricciones.

![Modificación-de-Bases-de-Datos-(3)](./img/Creación-de-Bases-de-Datos/Modificación-de-Bases-de-Datos/Modificación-de-Bases-de-Datos-(3).png)

Modificamos la tabla `Grupo` añadiendo restricciones.

![Modificación-de-Bases-de-Datos-(4)](./img/Creación-de-Bases-de-Datos/Modificación-de-Bases-de-Datos/Modificación-de-Bases-de-Datos-(4).png)

Modificamos la tabla `Profesor` añadiendo restricciones.

![Modificación-de-Bases-de-Datos-(5)](./img/Creación-de-Bases-de-Datos/Modificación-de-Bases-de-Datos/Modificación-de-Bases-de-Datos-(5).png)

Modificamos la tabla `Proyecto` añadiendo restricciones.

![Modificación-de-Bases-de-Datos-(6)](./img/Creación-de-Bases-de-Datos/Modificación-de-Bases-de-Datos/Modificación-de-Bases-de-Datos-(6).png)

Modificamos la tabla `Participa` añadiendo restricciones.

![Modificación-de-Bases-de-Datos-(7)](./img/Creación-de-Bases-de-Datos/Modificación-de-Bases-de-Datos/Modificación-de-Bases-de-Datos-(7).png)

Modificamos la tabla `Financia` añadiendo restricciones.

[Gist del ejercicio 1 (versión MySQL)](https://gist.github.com/xiaparga/7ee01446da81a75ce0d0c5c1ec7843ef)

Para el segundo ejercicio, vamos a hacer de la 2ª forma, es decir, importando un archivo `.sql`.

### Creación de base de datos importando un archivo <a name="creacion-de-base-de-datos-importando-un-archivo"></a>

![Creación-de-Bases-de-Datos-(13)](./img/Creación-de-Bases-de-Datos/Importación-de-un-archivo/Importación-de-un-archivo-(1).png)

Introducimos `sudo nano` y la ruta del archivo `.sql` para crearlo con el editor `Nano`.

![Creación-de-Bases-de-Datos-(14)](./img/Creación-de-Bases-de-Datos/Importación-de-un-archivo/Importación-de-un-archivo-(2).png)

![Creación-de-Bases-de-Datos-(15)](./img/Creación-de-Bases-de-Datos/Importación-de-un-archivo/Importación-de-un-archivo-(3).png)

![Creación-de-Bases-de-Datos-(16)](./img/Creación-de-Bases-de-Datos/Importación-de-un-archivo/Importación-de-un-archivo-(4).png)

Creamos el archivo con sus tablas y las tuplas y restricciones dentro de ellas. 

![Creación-de-Bases-de-Datos-(17)](./img/Creación-de-Bases-de-Datos/Importación-de-un-archivo/Importación-de-un-archivo-(5).png)

Introducimos `sudo mysql -u root < /home/usuario/Escritorio/ejercicio2.sql` para "exportar" el archivo `.sql` a MySQL.

[Gist del ejercicio 2 (versión MySQL)](https://gist.github.com/xiaparga/60a8b3260ab14f25a945bee0abea25c9)

[Volver al índice](#Índice)
