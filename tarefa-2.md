# Índice

- [MySQL](#mysql)
  - [Instalación y configuración de MySQL](#instalacion-y-configuracion-de-mysql)
    - [Servidor dedicado](#servidor-compartido)
    - [Servidor compartido](#servidor-compartido)
  - [Creación de bases de datos en MySQL](#creacion-de-bases-de-datos-en-mysql)
    - [Creación de base de datos a mano](#creacion-de-base-de-datos-a-mano)
    - [Creación de base de datos importando un archivo](#creacion-de-base-de-datos-importando-un-archivo)
  - [Estructura de una base de datos en MySQL](#muestra-de-estructura-y-de-datos-de-una-base-de-datos-en-mysql)
  

# MySQL <a name="mysql"></a>

## Instalación y configuración de MySQL <a name="instalacion-y-configuracion-de-mysql"></a>

Después de la resolución de los ejercicios propuestos por el profesor, vamos a instalar MySQL en Ubuntu a través de la terminal (que viene por defecto en esta distribución de Linux) y configurarlo según cuál sea el mejor flujo de trabajo (es decir, servidor compartido o servidor dedicado).

![Instalación de MySQL (1)](./img/Instalación/Instalación-de-MySQL-(1).png)

Introducimos `sudo apt update` para actualizar los repositorios de Ubuntu.

![Instalación de MySQL (2)](./img/Instalación/Instalación-de-MySQL-(2).png)

Introducimos `sudo apt install mysql-server` para instalar MySQL.

![Instalación de MySQL (3)](./img/Instalación/Instalación-de-MySQL-(3).png)

Introducimos `sudo mysql_secure_installation` para empezar a configurar la seguridad de MySQL.

A partir de aquí, la configuración es opcional pero imprescindible si queremos tener una seguridad alta en nuestras bases de datos.

![Configuración de MySQL (1)](./img/Configuración/Configuración-de-MySQL-(1).png)

Se nos pregunta si queremos configurar un plugin para validar contraseñas, respondemos `Y` o `y` para decir que si. Independientemente de lo que respondamos, tenemos que establecer una contraseña para el usuario **root** de MySQL. Ingresamos y luego confirmamos una contraseña de nuestra elección.

![Configuración de MySQL (2)](./img/Configuración/Configuración-de-MySQL-(2).png)

Se nos pregunta un nivel de política de validación de contraseña y elegimos el más alto posible.

![Configuración de MySQL (3)](./img/Configuración/Configuración-de-MySQL-(3).png)

Se nos pregunta la contraseña a introducir, se nos pregunta si queremos seguir con la contraseña introducida y respondemos `Y` o `y` para decir que si.

![Configuración de MySQL (4)](./img/Configuración/Configuración-de-MySQL-(4).png)

Se nos pregunta si queremos eliminar los usuarios anónimos de la instalación de MySQL y respondemos `Y` o `y` para decir que si.

![Configuración de MySQL (5)](./img/Configuración/Configuración-de-MySQL-(5).png)

Se nos pregunta si queremos eliminar los accesos remotos al usuario **root**, respondemos `Y` o `y` para decir que si.

![Configuración de MySQL (6)](./img/Configuración/Configuración-de-MySQL-(6).png)

Se nos pregunta si queremos eliminar la base de datos de prueba y los accesos a ella, respondemos `Y` o `y` para decir que si.

![Configuración de MySQL (7)](./img/Configuración/Configuración-de-MySQL-(7).png)

Se nos pregunta si queremos recargar las tablas de privilegios, respondemos `Y` o `y` para decir que si.

### Servidor compartido <a name="servidor-compartido"></a>

![Configuración de MySQL (8)](./img/Configuración/Servidor-Compartido/Servidor-Compartido-(1).png)

Accedemos al shell de MySQL introduciendo `sudo mysql`.

![Configuración de MySQL (9)](./img/Configuración/Servidor-Compartido/Servidor-Compartido-(2).png)

Introducimos `SELECT user,authentication_string,plugin,host FROM mysql.user;` para ver el método de autenticación que usa cada una de las cuentas de usuario de MySQL.

![Configuración de MySQL (10)](./img/Configuración/Servidor-Compartido/Servidor-Compartido-(3).png)

Introducimos `ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'contraseña';`.

Donde 'contraseña' es la contraseña a introducir para el usuario root.

![Configuración de MySQL (11)](./img/Configuración/Servidor-Compartido/Servidor-Compartido-(4).png)

Introducimos `FLUSH PRIVILEGES` para purgar privilegios, es decir, para decirle al servidor que vuelva a cargar las tablas `grant` e implemente sus nuevos cambios.

![Configuración de MySQL (12)](./img/Configuración/Servidor-Compartido/Servidor-Compartido-(5).png)

Introducimos `SELECT user,authentication_string,plugin,host FROM mysql.user;`para ver de nuevo el método de autenticación que usa cada una de las cuentas de usuario de MySQL.

![Configuración de MySQL (13)](./img/Configuración/Servidor-Compartido/Servidor-Compartido-(6).png)

Introducimos `exit` para salir del shell de MySQL.

[Volver al índice](#indice)

### Servidor dedicado <a name="servidor-dedicado"></a>

![Configuración de MySQL (14)](./img/Configuración/Servidor-Dedicado/Servidor-Dedicado-(1).png)

Alternativamente, para otras personas puede adaptarse mejor a su flujo de trabajo si se conectan a MySQL con un usuario dedicado, en este caso, introducimos `sudo mysql` para acceder al shell de MySQL. 

![Configuración de MySQL (15)](./img/Configuración/Servidor-Dedicado/Servidor-Dedicado-(2).png)

Si tenemos la autenticación de contraseña habilitada para **root** según se describió en los párrafos de arriba, introducimos `mysql -u root -p` y la contraseña del usuario **root** para acceder al shell de MySQL.

![Configuración de MySQL (16)](./img/Configuración/Servidor-Dedicado/Servidor-Dedicado-(3).png)

Para crear un usuario dedicado, introducimos `CREATE USER 'usuario'@'localhost' IDENTIFIED BY 'contraseña';`.

Donde 'contraseña' es la contraseña a introducir para el usuario actual.

![Configuración de MySQL (17)](./img/Configuración/Servidor-Dedicado/Servidor-Dedicado-(4).png)

Introducimos `GRANT ALL PRIVILEGES ON *.* TO 'usuario'@'localhost' WITH GRANT OPTION;` para concederle al usuario privilegios a todas las tablas dentro de la base de datos, así como autoridad para agregar, cambiar y eliminar privilegios de usuario.

![Configuración de MySQL (18)](./img/Configuración/Servidor-Dedicado/Servidor-Dedicado-(5).png)

Introducimos `exit` para salir del shell de MySQL.

![Configuración de MySQL (19)](./img/Configuración/Configuración-de-MySQL-(8).png)

Independientemente de cómo lo instalamos, MySQL debería haber empezado a ejecutarse automáticamente. Para probar esto, verificamos su estado introduciendo `sudo systemctl status mysql.service`.

Si MySQL no se está ejecutando, puede iniciarlo usando `sudo systemctl start mysql`.

![Configuración de MySQL (20)](./img/Configuración/Configuración-de-MySQL-(9).png)

Para una verificación adicional, puede tratar de conectarse a la base de datos usando la herramienta mysqladmin, que es un cliente que permite ejecutar comandos administrativos. Por ejemplo, este comando (`sudo mysqladmin -p -u root version`) dice que se conecte a MySQL como root (-u root), pida una contraseña (-p) y devuelva la versión.

[Volver al índice](#Índice)
