# Índice

- [MySQL](#mysql)
  - [Instalación y configuración de MySQL](#instalacion-y-configuracion-de-mysql)
    - [Servidor dedicado](#servidor-compartido)
    - [Servidor compartido](#servidor-compartido)
  - [Creación de bases de datos en MySQL](#creacion-de-bases-de-datos-en-mysql)
    - [Creación de base de datos a mano](#creacion-de-base-de-datos-a-mano)
    - [Creación de base de datos importando un archivo](#creacion-de-base-de-datos-importando-un-archivo)
  - [Estructura de una base de datos en MySQL](#muestra-de-estructura-y-de-datos-de-una-base-de-datos-en-mysql)

## Muestra de estructura y de datos de una base de datos en MySQL <a name="muestra-de-estructura-y-de-datos-de-una-base-de-datos-en-mysql"></a>

![Muestra-de-estructura-de-Base-de-Datos-(1)](./img/Visualización-de-Bases-de-Datos/Visualización-de-Bases-de-Datos-(1).png)

Introducimos `sudo mysql -u root -p` y la contraseña del usuario **root** para acceder al shell de MySQL.

![Muestra-de-estructura-de-Base-de-Datos-(2)](./img/Visualización-de-Bases-de-Datos/Visualización-de-Bases-de-Datos-(2).png)

Introducimos `SHOW DATABASES;` para mostrar la base de datos.

![Muestra-de-estructura-de-Base-de-Datos-(3)](./img/Visualización-de-Bases-de-Datos/Visualización-de-Bases-de-Datos-(3).png)

Introducimos `USE Investigacion;` para poder usar la base de datos 'Investigacion'.

![Muestra-de-estructura-de-Base-de-Datos-(4)](./img/Visualización-de-Bases-de-Datos/Visualización-de-Bases-de-Datos-(4).png)

Introducimos `SHOW TABLES` para mostrar las tablas de la base de datos 'Investigacion'.

![Muestra-de-estructura-de-Base-de-Datos-(5)](./img/Visualización-de-Bases-de-Datos/Visualización-de-Bases-de-Datos-(5).png)

Introducimos `DESC Departamento` para ver el contenido de la tabla `Departamento`.

![Muestra-de-estructura-de-Base-de-Datos-(6)](./img/Visualización-de-Bases-de-Datos/Visualización-de-Bases-de-Datos-(6).png)

Introducimos `DESC Financia` para ver el contenido de la tabla `Financia`.

![Muestra-de-estructura-de-Base-de-Datos-(7)](./img/Visualización-de-Bases-de-Datos/Visualización-de-Bases-de-Datos-(7).png)

Introducimos `DESC Grupo` para ver el contenido de la tabla `Grupo`.

![Muestra-de-estructura-de-Base-de-Datos-(8)](./img/Visualización-de-Bases-de-Datos/Visualización-de-Bases-de-Datos-(8).png)

Introducimos `DESC Participa` para ver el contenido de la tabla `Participa`.

![Muestra-de-estructura-de-Base-de-Datos-(9)](./img/Visualización-de-Bases-de-Datos/Visualización-de-Bases-de-Datos-(9).png)

Introducimos `DESC Profesor` para ver el contenido de la tabla `Profesor`.

![Muestra-de-estructura-de-Base-de-Datos-(10)](./img/Visualización-de-Bases-de-Datos/Visualización-de-Bases-de-Datos-(10).png)

Introducimos `DESC Programa` para ver el contenido de la tabla `Programa`.

![Muestra-de-estructura-de-Base-de-Datos-(11)](./img/Visualización-de-Bases-de-Datos/Visualización-de-Bases-de-Datos-(11).png)

Introducimos `DESC Proyecto` para ver el contenido de la tabla `Proyecto`.

![Muestra-de-estructura-de-Base-de-Datos-(12)](./img/Visualización-de-Bases-de-Datos/Visualización-de-Bases-de-Datos-(12).png)

Introducimos `DESC Sede` para ver el contenido de la tabla `Sede`.

![Muestra-de-estructura-de-Base-de-Datos-(13)](./img/Visualización-de-Bases-de-Datos/Visualización-de-Bases-de-Datos-(13).png)

Introducimos `DESC Ubicacion` para ver el contenido de la tabla `Ubicacion`.

![Muestra-de-estructura-de-Base-de-Datos-(14)](./img/Visualización-de-Bases-de-Datos/Visualización-de-Bases-de-Datos-(14).png)

Introducimos `USE NavesEspaciales;` para poder usar la base de datos 'NavesEspaciales'.

![Muestra-de-estructura-de-Base-de-Datos-(15)](./img/Visualización-de-Bases-de-Datos/Visualización-de-Bases-de-Datos-(15).png)

Introducimos `SHOW TABLES` para mostrar las tablas de la base de datos 'NavesEspaciales'.

![Muestra-de-estructura-de-Base-de-Datos-(16)](./img/Visualización-de-Bases-de-Datos/Visualización-de-Bases-de-Datos-(16).png)

Introducimos `DESC Camara` para ver el contenido de la tabla `Camara`.

![Muestra-de-estructura-de-Base-de-Datos-(17)](./img/Visualización-de-Bases-de-Datos/Visualización-de-Bases-de-Datos-(17).png)

Introducimos `DESC Dependencia` para ver el contenido de la tabla `Dependencia`.

![Muestra-de-estructura-de-Base-de-Datos-(18)](./img/Visualización-de-Bases-de-Datos/Visualización-de-Bases-de-Datos-(18).png)

Introducimos `DESC Habita` para ver el contenido de la tabla `Habita`.

![Muestra-de-estructura-de-Base-de-Datos-(19)](./img/Visualización-de-Bases-de-Datos/Visualización-de-Bases-de-Datos-(19).png)

Introducimos `DESC Planeta` para ver el contenido de la tabla `Planeta`.

![Muestra-de-estructura-de-Base-de-Datos-(20)](./img/Visualización-de-Bases-de-Datos/Visualización-de-Bases-de-Datos-(20).png)

Introducimos `DESC Raza` para ver el contenido de la tabla `Raza`.

![Muestra-de-estructura-de-Base-de-Datos-(21)](./img/Visualización-de-Bases-de-Datos/Visualización-de-Bases-de-Datos-(21).png)

Introducimos `DESC Servicio` para ver el contenido de la tabla `Servicio`.

![Muestra-de-estructura-de-Base-de-Datos-(22)](./img/Visualización-de-Bases-de-Datos/Visualización-de-Bases-de-Datos-(22).png)

Introducimos `DESC Tripulacion` para ver el contenido de la tabla `Tripulacion`.

![Muestra-de-estructura-de-Base-de-Datos-(23)](./img/Visualización-de-Bases-de-Datos/Visualización-de-Bases-de-Datos-(23).png)

Introducimos `DESC Visita` para ver el contenido de la tabla `Visita`.

[Volver al índice](#Índice)
