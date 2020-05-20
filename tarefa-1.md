# Índice
- [Introducción](#introduccion)
- [Fórmulas](#formulas)
  - [DDL](#ddl)
    - [`CREATE`](#create)
    - [`DROP`](#drop)
    - [`ALTER`](#alter)
  - [DML](#dml)
    - [`INSERT`](#insert)
    - [`UPDATE`](#update)
    - [`DELETE`](#delete)


# Introducción <a name="introduccion"></a>
SQL tiene 1 lenguaje y 6 sublenguajes, que son los siguientes:

  - DQL (Data Query Language): `SELECT`. Opera sobre los datos (de la base de datos).
  - DDL (Data Definition Language): Existen 3 operaciones básicas: `CREATE`, `ALTER` y `DROP`. Opera sobre los objetos de la base de datos.
  - DML (Data Manipulation Language): Existen 3 operaciones básicas: `INSERT`, `UPDATE` y `DELETE`. Opera sobre los datos (de la base de datos).
  - TCL (Transaction Control Language): Existen 2 operaciones básicas: `COMMIT` y `ROLLBACK`.
  - DCL (Data Control Language): Existen 2 operaciones básicas: `GRANT` y `REVOKE`.
  - SCL (Session Control Language): Existe 1 operación básica: `ALTER SESSION`.

  Los 3 primeros sublenguajes forman parte del núcleo de SQL.

[Volver al índice](#Índice)

Antes de comenzar, vamos a ver los tipos de datos que vamos a usar.

|Tipos de datos (Dominios)|Descripción|
|--|--|
|INTEGER||
|DECIMAL|Preciso|
|REAL|No preciso|
|CHAR|Longitud fija (limitada)|
|VARCHAR|Longitud variable (limitada)|
|TEXT|Longitud variable (ilimitada)|
|DATE|día, mes, año|
|TIME|Hora, minutos, segundos... [zona horaria]|
|TIMESTAMP|DATE + TIME|
|BOOLEAN|TRUE (1), FALSE (0), NULL|
|INET|
|CIDR|
|UUID|
|MONEY|
|JSON|

# Fórmulas <a name="drop"></a>

## DDL <a name="ddl"></a>

### `CREATE` <a name="create"></a>

La sentencia `CREATE` permite crear objetos de datos, como nuevas bases de datos, tablas, vistas y procedimientos almacenados. 

Para crear una base de datos, usaríamos esta sintaxis.

```SQL
CREATE DATABASE myDB;
```

Una desventaja de usar esta fórmula es que hay problemas con permisos. Es mejor utilizar la que se ve a continuación.

```SQL
CREATE SCHEMA myOtherDB;
```

Para crear un esquema o una base de datos si previamente no existe la base de datos, usaríamos esta sintaxis.

```SQL
CREATE (SCHEMA|DATABASE)
[IF NOT EXISTS] <nombre-de-la-base-de-datos>
[CHARACTER SET <nombreConelCharset>]
COLLATE;
```

Para crear una tabla que contiene un identificador, un nombre, apellidos y fecha de nacimiento en la base de datos, usaríamos esta sintaxis.

```SQL
CREATE TABLE Alumno (
  id INTEGER PRIMARY KEY,
  nombre NCHAR(50) NOT NULL,
  apellidos NCHAR(200),
  nacido DATE
);
```

Para crear una restricción con su clave primaria y los atributos de la misma, usaríamos esta sintaxis.

```SQL
[CONSTRAINT <nombre-de-la-restriccion>]
  PRIMARY KEY (<atributos>),
```

Un ejemplo en SQL sería así:

```SQL
CONSTRAINT PK_WORLD
  PRIMARY KEY (name, continent),
```

Para asignar una clave primaria a un atributo, podríamos usar esta sintaxis:

```SQL
name CHAR(80) PRIMARY KEY,
```

Esta sería la forma completa de crear una restricción, en este caso es una clave ajena que referencia a una tabla que asignemos nosotros.

```SQL
[CONSTRAINT <nombre-de-la-restriccion>]
  FOREIGN KEY (<atributos>)
    REFERENCES <nombre-de-la-tabla-referenciada>
      [(<atributos-referenciados>)]
  [MATCH FULL | PARTIAL]
  [ON DELETE CASCADE | NO ACTION | SET NULL | SET DEFAULT]
  [ON UPDATE CASCADE | NO ACTION | SET NULL | SET DEFAULT]
```

Estos serían los posibles valores de `ON DELETE`.

```SQL
[ON DELETE | NO ACTION]
[ON DELETE | NO ACTION | CASCADE]
[ON DELETE | NO ACTION | SET NULL]
[ON DELETE | NO ACTION | SET NULL | SET DEFAULT]
```

Donde:

`MATCH FULL`: Si se agrega después de la declaración `REFERENCES`, no puede coincidir un valor nulo y otro no nulo con la clave externa, pero pueden coincidir valores nulos con la clave externa.

`MATCH PARTIAL`: Si se agrega después de la declaración `REFERENCES`, cualquier no nulo debe coincidir con la clave externa.

`NO ACTION`: realiza la comprobación de integridad referencial después de tratar de modificar la tabla.

`CASCADE`: Cada vez que se eliminan o se actualizan las filas de la tabla maestra, se eliminarán o actualizarán las respectivas filas de la tabla hija.

`SET NULL`: El valor de la referencia afectada se cambia a `NULL`. Cada vez que se elimina o actualiza el registro en la tabla padre, establece a `NULL` las columnas de la clave ajena en la tabla hija, para ello las columnas de la tabla hija **no** han de haber sido definidas como `NOT NULL`.

`SET DEFAULT`: El valor de la referencia afectada se cambia al valor predeterminado.

Para crear una restricción que sea igual a una clave ajena y que sus atributos sean únicos, usaríamos esta sintaxis:

```SQL
[CONSTRAINT <nombre-de-la-restricción>]
            FK_
            LIKE 'FK_%'
  UNIQUE (<atributos>),
```

Para crear una restricción en la cual sus atributos sean únicos, usaríamos esta sintaxis:

```SQL
[CONSTRAINT <nombre-de-la-restricción>]
  UNIQUE (<atributos>),
```

Mismo formato que `PRIMARY KEY`.

Para crear una restricción aplazable o que se aplique inmediatamente, usaríamos esta sintaxis:

```SQL
[CONSTRAINT <nombre-de-la-restricción>]
  CHECK predicado(atributos)
  [[NOT]] DEFERRABLE]
  [INITIALLY INMEDIATE|DEFERRABLE]
```

Para verificar si se cumple una condición, usaríamos esta sintaxis:

```SQL
CHECK balance > 0
```

Para verificar si el saldo es mayor que cualquier saldo de un empleado del departamento 'A', un ejemplo en SQL sería así:

```SQL
CHECK saldo >= (
      SELECT saldo
      FROM empleado
      WHERE departamento = 'A'),
```

Para definir nuestros propios tipos de datos, ya que hay veces que no se puede asignar alguno de los tipos mencionados anteriormente, usaríamos esta sintaxis:

```SQL
CREATE DOMAIN miDominio;
```

Para definir un dominio (como un tipo de código que tenga como máximo 5 caracteres), un ejemplo en SQL sería así:

```SQL
CREATE DOMAIN Tipo_Codigo CHAR(5);
```

### `DROP` <a name="drop"></a>

La sentencia `DROP` elimina un objeto de la base de datos. Puede ser una tabla, vista, índice, disparador, función, procedimiento o cualquier objeto que el motor de la base de datos soporte. Se puede combinar con la sentencia `ALTER`. 

```SQL
DROP SCHEMA
[IF EXISTS] <nombre-de-la-base-de-datos>
```

Para eliminar una tabla (si existe previamente esa tabla) con sus datos en cascada o intentar eliminarla pero que tenga objetos dependientes, y que al final no se pueda, usaríamos esta sintaxis:

```SQL
DROP TABLE
[IF EXISTS] <nombre-de-la-tabla>
[CASCADE | RESTRICT];
```

### `ALTER` <a name="alter"></a>

La sentencia `ALTER` permite modificar la estructura de una tabla u objeto. Se pueden agregar/quitar campos a una tabla, modificar el tipo de un campo, agregar/quitar índices a una tabla, etc.

Para modificar una tabla añadiendo o eliminando columnas o restricciones, usaríamos esta sintaxis:

```SQL
ALTER TABLE <nombre-de-la-tabla>
ADD [COLUMN] <atributo> <columnas> <dominio>...
DROP COLUMN <atributo> [CASCADE|RESTRICT]
ADD <restriccion>
DROP <restriccion>;
```

[Volver al índice](#Índice)

## DML <a name="dml"></a>

### `INSERT` <a name="insert"></a>

La sentencia `INSERT` de SQL agrega uno o más registros a una (y sólo una) tabla en una base de datos relacional.

Para insertar un atributo con sus valores, usaríamos esta sintaxis:

```SQL
INSERT INTO <nombre-de-la-tabla>
[(<atributo1, atributo2>, ...)]
(VALUES(<valor1>, <valor2>, ...) | SELECT...);
```

`SELECT` tiene que tener el mismo número de columnas, mismos dominios, como por ejemplo, (`DATETIME`, `NCHAR`, `INTEGER`).

Para insertar un elemento con su código de producto y precio, usaríamos esta sintaxis:

```SQL
(1, 'Cheese', 9.99),
(2, 'Bread', 1.99),
(3, 'Milk', 2.99);
```

### `UPDATE` <a name="update"></a>

La sentencia `UPDATE` es utilizada para modificar los valores de un conjunto de registros existentes en una tabla.

Para actualizar una tabla, usaríamos esta sintaxis:

```SQL
UPDATE <nombre-de-la-tabla>
SET <atributo1> = <valor1>,
    <atributo2> = <valor2>,
    ...
[WHERE <predicado>];
```

Para actualizar la tabla `world` de forma que un atributo tenga de nombre 'España', que su continente sea 'África' y que ese atributo se llame previamente 'Spain', un ejemplo en SQL sería así:

```SQL
UPDATE world
SET name = 'España',
continent = 'Africa'
WHERE name = 'Spain';
```

### `DELETE` <a name="delete"></a>

La sentencia `DELETE` borra uno o más registros existentes en una tabla.

Para eliminar algún atributo de una tabla, usaríamos esta sintaxis:

```SQL
DELETE FROM
<nombre-de-la-tabla>
[WHERE <predicado>];
```

Para eliminar la población de la tabla `world`, un ejemplo en SQL sería así:

```SQL
DELETE FROM world
WHERE population > 100000000;
```

[Volver al índice](#Índice)
