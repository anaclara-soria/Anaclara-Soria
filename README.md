# Proyecto Tina Cafe

**Alumna:** Anaclara Soria

**Curso:** SQL

**Comisión:** 59430

**Docente:** Anderson Ocaña

**Tutor:** Nicolas Maugeri  

## Presentacion
(https://docs.google.com/presentation/d/1SSa6XDjAFYpgenyTD2TwJ4lAl4FZKZaCAo9YB8wfwRk/edit#slide=id.p)

---

## Introduccion
Mi nombre es Anaclara Soria, curso en Coderhouse Base de datos en SQL, y presentare como proyecto una base de datos basado en una cafeteria (ficticio) petfriendly libre de gluten dedicada a ofrecer una experiencia unica en un ambiente calido y moderno con sabores de calidad.

## Situacion Problematica

Actualmente, mi cafeteria enfrenta varios problemas en la administracion de sus ventas y pedidos. A raiz del incremento de la demanda, se ha vuelto difícil medir la rentabilidad real del negocio, realizar un correcto seguimiento de ventas, controlar el inventario y actualizar la informacion referida a clientes, ordenes y empleados. 

## Objetivo
Crear un sistema que permita almacenar y manipular toda esta informacion con el objetivo de tenemos mejor visibilidad de los resultados del negocio y tomar decisiones efectivas.

## Diagrama Entidad - Relacion

![image](https://github.com/user-attachments/assets/47a24e56-1927-426a-8dcb-9df489397dd1)

**Resumen de los Datos Insertados:**

- Categoria_producto: Diez categorías: Cafe, Te, Limonada, Aguas Saborizadas, Pasteleria, Cookies, Sandwiches, Frutas, Ensaladas y Panaderia.

- Producto: Se han añadido diez productos en diez categorías diferentes.

- Proveedor: Diez proveedores asociados a los productos.

- Cliente: Diez clientes con diferentes correos electrónicos, números de teléfono y DNI.

- Empleado: Diez empleados con distintos puestos en el café.

- Orden: Diez órdenes realizadas por diez clientes, cada una asociada con un producto y un empleado.

- Detalle_orden: Diez detalles de orden con las cantidades de los productos comprados, el metodo de entrega y los comentarios asociados a cada orden.

- Pagos: Diez pagos diferentes asociados a cada orden y suministrando el dato de la fecha de pago, el estado de la transaccion, el metodo de pago y el descuento aplicado.

- Inventario: Esta tabla proporciona la informacion referida a el stock de cada producto, el estado de los productos, la fecha de ingreso y de vencimiento. 

- Envios: Cuatro envios realizados en Zarate con el dato del estado de cada uno de ellos.

- Calificaciones: Calificaciones por cada pedido realizado clasificando los comentarios en 3 tipos (producto, servicio o atencion al cliente).


## Tablas y Descripcion de Campos

**1) Proveedor**

• Descripción: Almacena información sobre los proveedores de productos. 

• Campos: 

id_proveedor: int (PK, auto_increment)

id_producto: int - Referencia al producto que proporciona.

Nombre: VARCHAR(200) - Nombre del proveedor.

Telefono: VARCHAR(200) - Número de teléfono del proveedor.

Direccion: VARCHAR(200) - Dirección del proveedor.

Email: VARCHAR(200) (UNIQUE) - Correo electrónico del proveedor.


**2) Producto** 

• Descripción: Almacena información sobre los productos ofrecidos en el café. 

• Campos:

id_producto: int (PK, auto_increment)
Identificador único del producto.

id_categoria_producto: int
Referencia a la categoría del producto.

Tipo_producto: VARCHAR(200) 

Nombre: VARCHAR(200) 
Nombre del producto

Precio: DECIMAL(10,2). Precio del producto. 

stock: int
Cantidad de productos disponibles en ese momento.

**3) Categoria_producto** 

• Descripción: Define las categorías a las que pertenecen los productos. 

• Campos: 

id_categoria_producto: int (PK, auto_increment) - Identificador único de la categoría.

Nombre_categoria: VARCHAR(200). Nombre de la categoría. 

Descripcion: VARCHAR(200). Descripción de la categoría.

fecha_actualizacion: DATE - Fecha en que se actualizo cada categoria, incorporando o eliminando productos.

Subcategoria: VARCHAR(200)

**4) Cliente** 

• Descripción: Almacena información sobre los clientes. 

• Campos: 

id_cliente: int (PK, auto_increment) - Identificador único del cliente. 

Nombre: VARCHAR(200). Nombre del cliente. 

DNI: char(8). El objetivo de este campo es tener una nocion del publico promedio que nos consume.

Email: VARCHAR(200) (UNIQUE) - Correo electrónico del cliente.

Telefono: VARCHAR(200) - Número de teléfono del cliente.

**5) Empleado** 

• Descripción: Almacena información sobre los empleados del café. 

• Campos: 

id_empleado: int (PK, auto_increment) - Identificador único del empleado. 

Nombre: VARCHAR(200) - Nombre del empleado. 

Direccion: VARCHAR(200) - Dirección del empleado. 

Email: VARCHAR(200) (UNIQUE) - Correo electrónico del empleado.

Telefono: VARCHAR(100) - Número de teléfono del empleado. 

Puesto: VARCHAR(200) - Puesto de trabajo del empleado.

**6) Orden** 

• Descripción: Almacena información sobre las órdenes realizadas por los clientes. 

• Campos:

id_orden: int (PK, auto_increment) - Identificador único de la orden. 

id_cliente: int - Referencia al cliente que realiza la orden. 

id_producto: int - Referencia al producto ordenado. 

id_empleado: int - Referencia al empleado que gestiona la orden. 

fecha: DATE - Fecha en que se realizó la orden.

Estado: pendiente, en proceso, completada, cancelada o pagada a traves de un ENUM.


**7) Pagos** 

• Descripción: Almacena información sobre los pagos realizados por las órdenes. 

• Campos:

id_pagos: int (PK, auto_increment) - Identificador único del pago.

id_detalle_orden: int - Referencia a los detalles de la orden pagada.

fecha: DATE - Fecha del pago.

Descuento: decimal (5,2).

Metodo de pago: distintas opciones de pago a traves de un ENUM (en efectivo, tarjeta o a traves de mercado pago).

Estado de pago: pendiente, completado, fallido, reembolsado. El objetivo de este campo es visualizar rapidamente si el sistema de cobros presenta algun problema.

**8) Detalle_orden** 

• Descripción: Almacena los detalles de cada orden, incluyendo los productos y cantidades. 

• Campos: 

id_detalle_orden: int (PK, auto_increment) - Identificador único del detalle de la orden.

id_orden: int - Referencia a la orden correspondiente. 

id_producto: int - Referencia al producto en la orden. 

comentarios (VARCHAR 200). El objetivo es tomar nota de los comentarios mas recurrentes de los clientes y mejorar el servicio y las opciones de productos. Ejemplo, sin azucar, sin sal, sin tacc, con leche vegana, etc.

cantidades: DECIMAL(10,2) - Cantidad del producto en la orden.

Metodo_entrega: Delivery o consumo en el local.

**9) Calificaciones** 

• Descripción: Almacena las calificaciones tanto positivas como negativas de cada cliente en cada orden. 

• Campos: 

id_calificacion: int (PK, auto_increment) - Identificador único del detalle de la orden.

id_cliente: int - (FK) 

id_orden: int - (FK) 

comentarios (TEXT). El objetivo es tomar nota de los las criticas positivas y negativas de los clientes para mejorar el servicio y satisfacer sus necesidades. 

tipo_comentario: el objetivo es categorizar si el comentario hace referencia al producto, al servicio, a la atencion, etc.

Calificacion: INT . Calificacion del 1 al 5 siendo 5 la mejor puntuacion.

**10) Envios** 

• Descripción: Almacena informacion referida a los envios a domicilio.. 

• Campos: 

id_envio: int (PK, auto_increment) - Identificador único del detalle de la orden.

id_orden: int - (FK) 

id_empleado: int - (FK). El objetivo de este campo es identificar la correcta distribucion de envios entre los repartidores del negocio.

Direccion: VARCHAR (200). El objetivo es detectar el radio de los envios mas frecuentes para evaluar cuantos repartidores se necesitan para abastecer la demanda.

fecha: date.

Estado: pendiente, en transito o entregado.

**11) Inventario** 

• Descripción: Almacena informacion referida al stock de productos por categoria con el objetivo de mantener una buena administracion y anticiparse a realizar nuevas ordenes a tiempo.

• Campos: 

id_inventario: int (PK, auto_increment) - Identificador único del detalle de la orden.

id_producto: int - (FK) 

stock: INT

fecha_ingreso: DATE. Fecha en que ingreso la ultima mercaderia al local.

fecha_vencimiento: DATE. Proxima fecha de vencimiento de los productos.

Estado_producto: Categoriacion en nuevo, en promocion, defectuoso o normal. El objetivo es organizar es mejorar la administracion del stock.


## Relaciones

• producto tiene una relación de clave foránea con categoria_producto.

• orden tiene relaciones de clave foránea con cliente y empleado.

• pagos tiene una relación de clave foránea con detalle_orden.

• detalle_orden tiene relaciones de clave foránea con orden y producto. 

• proveedor tiene una relación de clave foránea con producto.

• calificaciones tiene una relación de clave foránea con cliente y orden.

• envios tiene una relación de clave foránea con empleado y orden.

• inventario tiene una relación de clave foránea con producto.


**Problemas que Resuelve:**

*Gestión de Inventario:* Permite llevar un control de los productos por categoría y por proveedor.

*Gestión de Empleados:* Organiza la información del personal y su relación con las órdenes.

*Gestión de Proveedores:* Organiza la información de los proveedores y su relación con cada producto.

*Control de Pagos:* Facilita el seguimiento de los pagos realizados por los clientes.

*Análisis de Ventas:* Permite obtener conclusiones de ventas por producto y categoría permitiendo analizar la tendencia de las mismas y la rentabilidad del negocio. También permite tener mayor control sobra las ventas por empleado y evaluar su rendimiento.

Esta estructura permite un manejo eficiente y organizado de la información del café, facilitando la toma de decisiones y mejorando el servicio al cliente.





 # Objetos de la base de datos

 ## Vistas aplicadas y Descripciones

*`Vista_Ventas_por_periodo`*: Sumatoria de los precios de los productos vendidos.
   Objetivo: identificar los periodos con mayores y menores ventas para tomar medidas al respecto.

  **Tablas que componen la vista:** 
- *Orden*: Proporciona la fecha de cada orden.
- *Detalle de orden*: Proporciona las cantidades de cada id de productos por cada id de orden
- *Producto*: Proporciona el precio de cada producto.

Ejemplo de consulta:
```sql
SELECT * FROM vw_ventas_por_periodo;
```

*`Vista_Ventas_por_producto`*: Total de unidades vendidas y la suma de ingresos por cada producto con el objetivo de visualizar que productos son mas populares.

 **Tablas que componen la vista:** 

- *Detalle de orden*: Proporciona las cantidades de cada id de productos por cada id de orden
- *Producto*: Proporciona el precio de cada producto.

Ejemplo de consulta:
```sql
SELECT * FROM vw_ventas_por_producto;
```
  
*`Vista_Ventas_por_categoria`*: Total de ventas y unidades por cada categoría de producto (e.g., bebidas, comidas, snacks).

**Tablas que componen la vista:** 

- *Detalle de orden*: Proporciona las cantidades de cada id de productos por cada id de orden
- *Producto*: Proporciona el precio de cada producto.
- *Categoria de producto*: Proporciona el nombre de cada categoria de producto.

Ejemplo de consulta:
```sql
SELECT * FROM vw_ventas_por_categoria;
```
  
*`Vista_Ventas_por_empleado`*: Analizar qué empleados están generando más ingresos de acuerdo a las ordenes colocadas

**Tablas que componen la vista:** 

- *Detalle de orden*: Proporciona las cantidades de cada id de productos por cada id de orden
- *Producto*: Proporciona el precio de cada producto.
- *Orden*: Funciona como puente entre tabla producto y empleado.
- *Empleado*: Proporciona el nombre de cada empleado.

Ejemplo de consulta:
```sql
SELECT * FROM vw_ventas_por_empleado;
```

 ## Funciones

- *`Pedidos_por_empleado`*: Función que declara la cantidad de pedidos tomados por empleado. 
- *`Producto_mas_vendido`*: Función los productos mas vendidos.

---

## 1. Pedidos_por_empleado

*`Objetivo`*: Proporcionar la cantidad de pedidos tomados por cada empleado a raiz de la informacion proporcionada en las tablas de orden y empleados con el objetivo de monitorear que la carga de trabajo se encuentre correctamente balanceada.

**Tablas Involucradas**:

- *`Orden`*: La tabla que almacena el id de cada orden (pedido) realizada.
- *`Empleado`*: La tabla que almacena el nombre de cada empleado y el id de cada orden (pedido) realizada.

---

### Descripción de la Función:
La función Pedidos_por_empleado toma como parámetro el id_empleado y realiza lo siguiente:

#### a.	Declara una variable resultado de tipo INT para almacenar la sumatoria de pedidos tomados por cada empleado.
#### b.	Realiza una consulta SELECT que:
- Suma la cantidad de ordenes en la tabla Orden.
- Selecciona el nombre proveniente de la tabla Empleado.  
#### c.	Realiza un LEFT JOIN para:
- Unificar la tabla orden (contiene el campo id_orden) con la tabla empleados (contiene el campo nombre) a traves del campo id_orden.
#### d.	Realiza un GROUP BY para:
- Ordenar los pedidos por nombre de empleado.
#### e.	La función devuelve el resultado, que es la cantidad de ordenes por empleado.

```sql
DROP FUNCTION IF EXISTS tina_cafe.fx_total_pedidos;
DELIMITER //
CREATE FUNCTION tina_cafe.fx_total_pedidos (_empleado VARCHAR (200))
RETURNS INT
READS SQL DATA

BEGIN
DECLARE resultado INT default 0;
select 
e.nombre,
count(o.id_orden) as total_pedidos into resultado
from orden as o
left join empleado as e
on o.id_empleado = e.id_empleado
where e.nombre like _empleado
group by e.id_empleado;

RETURN resultado;
END //
Delimiter ;

```

## 2. Producto_mas_vendido

*`Objetivo`*: Proporcionar el nombre del producto con mas ventas con el objetivo de tener visibilidad de la rentabilidad del negocio y poder realizar estrategias mas eficientes.

**Tablas Involucradas**:

- *`Producto`*: La tabla que almacena el nombre de cada producto.
- *`Detalle_orden`*: La tabla que almacena el id de producto.

---

### Descripción de la Función:
La función Producto_mas_vendido toma como parámetro el id_producto y realiza lo siguiente:

#### a.	Declara una variable resultado de tipo VARCHAR para almacenar el nombre del producto.
#### b.	Realiza una consulta SELECT que:
- Selecciona el nombre proveniente de la tabla producto. 
#### c.	Realiza un INNER JOIN para:
- Unificar la tabla producto (contiene el campo nombre) con la tabla detalle_orden (contiene el cantidades) a traves del campo id_producto.
#### d.	Realiza un GROUP BY para:
- Ordenar los pedidos por id_producto.
#### e.	Realiza un ORDER BY SUM (cantidades) para:
- Ordenar los productos por cantidades vendidas.
#### f.	La función devuelve el resultado, que son los dos productos con mayores unidades vendidas.

```sql
DROP FUNCTION IF EXISTS tina_cafe.fx_producto_mas_vendido;
DELIMITER //
CREATE FUNCTION tina_cafe.fx_producto_mas_vendido (_producto VARCHAR (200)) 
RETURNS VARCHAR(200)
READS SQL DATA

BEGIN
DECLARE valor_retorno VARCHAR(200);

SELECT 
p.nombre INTO valor_retorno
FROM producto as p
INNER JOIN detalle_orden AS do 
ON p.id_producto = do.id_producto
GROUP BY p.id_producto
ORDER BY SUM(do.cantidades) DESC
LIMIT 2;
    
RETURN valor_retorno;
END //
Delimiter ;
```

# Store Procedure

- *`RegistrarProveedor`*: Registrar un nuevo proveedor
- *`RegistrarOrden`*: Registrar una nueva orden. 
---

## 1. RegistrarProveedor
*`Objetivo`*: Permite insertar nuevos proveedores en la base de datos proveedor.

**Tablas Involucradas**:

- *`Proveedor`*: Recibe los datos proporcionados como parámetros en el procedimiento.
---

### Descripción del Procedimiento:
El procedimiento almacenado RegistrarProveedor recibe los siguientes parámetros:
- p_id_producto: Productos que ofrece el proveedor
- p_nombre: Nombre del proveedor
- p_telefono: Telefono del proveedor
- p_direccion: Direccion del proveedor.
- p_email: Email del proveedor.

### Lógica Interna:

#### 1. INSERT INTO Proveedor: Inserta los valores proporcionados por los parámetros en la tabla Proveedor.

#### 2. Ejemplo de uso
---
### Registrar un proveedor
Supongamos que deseas registrar un nuevo cliente llamado "Proveedor Packaging" con los siguientes datos:
- id_producto: 10
- nombre: 'Panaderia Lucianti'
- Teléfono: 3487-567890
- Direccion: 'Valentin Alsina 1317'
- Email: 'lucianti@gmail.com
```sql
DELIMITER //
CREATE PROCEDURE Registrar_proveedor(
    IN p_id_producto INT,
    IN p_nombre_proveedor VARCHAR(200),
    IN p_telefono_proveedor VARCHAR(200),
    IN p_direccion_proveedor VARCHAR(200),
    IN p_email_proveedor VARCHAR(200)
)
BEGIN
    INSERT INTO proveedor (id_producto, nombre_proveedor, telefono_proveedor, direccion_proveedor, email_proveedor)
    VALUES (10, 'Panaderia Lucianti', '3487-567890', 'Valentin Alsina 1317', 'lucianti@gmail.com');
    
END //
DELIMITER ;

```
#### Ejecutar procedimiento: 
```sql

CALL Registrar_proveedor(10, 'Panaderia Lucianti', '3487-567890', 'Valentin Alsina 1317', 'lucianti@gmail.com');

```
#### Resultado esperado: 
El procedimiento inserta un nuevo registro en la tabla proveedor con los datos proporcionados.

---
#### Validación: 
Consulta para verificar que el proveedor fue registrado correctamente:
```sql
SELECT * FROM Proveedor;
```
---

## 2. RegistrarOrden

*`Objetivo`*: Permite insertar nuevas ordenes en la base de datos orden.

**Tablas Involucradas**:

- *`Orden`*: Recibe los datos proporcionados como parámetros en el procedimiento.

---

### Descripción del Procedimiento:
El procedimiento almacenado RegistrarOrder recibe los siguientes parámetros:
- p_id_cliente: identificacion de cada cliente.
- p_id_empleado: identificacion de cada empleado.
- p_id_producto: identificacion de cada producto.
- p_fecha: fecha de cada orden.

### Lógica Interna:

#### 1. INSERT INTO Orden: Inserta los valores proporcionados por los parámetros en la tabla Orden.

#### 2. Ejemplo de uso

---

### Registrar una orden de un cliente.
Supongamos que deseas registrar un nuevo cliente con los siguientes datos:
- id_cliente: 2
- id_empleado: 2
- Fecha: '2024-12-20'
- Estado_orden: 'Completada'
```sql
DELIMITER //
CREATE PROCEDURE registrar_orden(
    IN p_id_cliente INT,
    IN p_id_empleado INT,
    IN p_fecha_orden DATE,
    IN p_Estado_orden ENUM('pendiente', 'en proceso', 'completada', 'cancelada', 'pagada')
    )    
BEGIN
    INSERT INTO orden (id_cliente, id_empleado, fecha_orden, estado_orden)
    VALUES (2, 2, '2024-12-20','Completada');
    
END //
DELIMITER ;

```
#### Ejecutar procedimiento: 
```sql
CALL registrar_orden(2, 2, '2024-12-20','Completada');
```
#### Resultado esperado: 
El procedimiento inserta un nuevo registro en la tabla orden con los datos proporcionados.

---
#### Validación: 
Consulta para verificar que la orden fue registrada correctamente:
```sql
SELECT * FROM Orden;
```
---

# Triggers

Ambos triggers tienen el propósito de asegurar la integridad de la base de datos, actualizando automáticamente el stock y garantizando que los pagos solo se realicen en órdenes válidas.

- *`Actualizar_stock_producto`*
- *`Prevenir_pago_para_orden_cancelada`*
---

## 1. Actualizar_stock_producto
*`Objetivo`*: Este trigger tiene como objetivo actualizar el stock de los productos en la tabla producto cuando se crea una nueva orden. Cuando se inserta un registro en la tabla detalle_orden, que está relacionada con la orden, el stock de los productos que están siendo comprados debe ser disminuido en la cantidad especificada en Cantidades_orden.

*`Accion esperada`*: Cuando se inserte una nueva orden en la tabla detalle_orden, el trigger debe reducir el stock de los productos involucrados en la orden.

**Tablas Involucradas**:

- *`Producto`* : Esta tabla nos permite obtener el stock actual del producto a traves del ID del producto.
- *`Detalle_orden`* : Esta tabla nos permite actualizar el stock de cada producto restando la cantidad vendida cada vez que se agrega una nueva orden.

### Ejemplo: Se crea una orden con un producto con ID 1 (Café) en la tabla detalle_orden:

```sql
INSERT INTO detalle_orden (id_orden, id_producto, comentarios_orden, Cantidades_orden, Metodo_entrega)
VALUES (1, 1, 'Cortado', 2.00, 'consumo en local');

```
#### Resultado esperado: El stock del producto con id_producto = 1 (Café) debería reducirse en la cantidad indicada en Cantidades_orden (en este caso 2).
---

## 2. Prevenir_pago_para_orden_cancelada
*`Objetivo`*: Este trigger tiene como objetivo prevenir la inserción de un pago en la tabla pagos si la orden asociada está en estado "cancelada". Si el estado de la orden es "cancelada", el pago no debería ser procesado.

*`Accion esperada`*: Cuando se intente insertar un registro en la tabla pagos, el trigger debe verificar si la orden asociada a ese pago está en estado "cancelada". Si la orden está en estado "cancelada", la inserción del pago debe ser rechazada.

**Tablas Involucradas**:

- *`Pagos`* 
- *`Detalle_orden`* : Esta tabla nos permite obtener el estado de la orden.

### Ejemplo: Se quiere insertar un pago para una orden con id_orden = 8, que está en estado "cancelada"

```sql

INSERT INTO pagos (id_detalle_orden, fecha_pago, Descuento_pago, Metodo_pago, Estado_pago)
VALUES (8, '2024-12-10', 0.2, 'efectivo', 'completado');

```
#### Resultado esperado: El pago no debería insertarse en la tabla pagos si el estado de la orden asociada es "cancelada". El SQL de inserción debería dar un error indicando que no se puede procesar el pago para una orden cancelada.
---

# Gestión de Roles, Usuarios y Privilegios en MySQL

## Definición de Roles y Privilegios

### Anaclara Soria (Administradora de Base de Datos)
- **Rol:** Administrador.
- **Descripción:** Responsable de la gestión y el manipuleo de la base de datos.
- **Privilegios:** 
  - Acceso total a todas las tablas.
  - Capacidad para gestionar usuarios y asignar privilegios (GRANT, REVOKE).
  - Permisos: `SELECT`, `INSERT`, `UPDATE`, `DELETE`, y más.

### Lucia Castro (Usuario de Solo Lectura)
- **Rol:** Usuario con privilegios limitados.
- **Descripción:** Acceso a datos almacenados sin capacidad de modificación.
- **Privilegios:** 
  - Permiso solo para `SELECT` en tablas como `Calificaciones`, `Envios`, `Cliente`, 'Orden', 'Pagos'.

### Manuela Baxovanos (Usuario con Permisos de Escritura Limitados)
- **Rol:** Usuario con permisos restringidos.
- **Descripción:** Modificaciones permitidas en áreas específicas de la base de datos.
- **Privilegios:** 
  - `INSERT`, `UPDATE`, y `SELECT` en tablas como `Producto`, `Categoria_producto`, `Inventario`, `Proveedor`.

---

## Creación de Usuarios y Asignación de Privilegios

Asegura que cada persona tenga accesa solo a los datos que corresponden segun su responsabilidad en el negocio, protegiendo la integridad y confidencialidad de la información. La implementación de un modelo de roles y privilegios facilita la administración y seguridad del sistema.

### Paso 1: Crear los usuarios
```sql
CREATE USER 'anaclara'@'%' IDENTIFIED BY 'Anaclara';
CREATE USER 'lucia'@'%' IDENTIFIED BY 'Lucia';
CREATE USER 'manuela'@'%' IDENTIFIED BY 'Manuela';
```
### Paso 2: Asignar privilegios
Anaclara Soria (Administrador)
```sql
GRANT ALL PRIVILEGES ON *.* TO 'anaclara'@'%' WITH GRANT OPTION;
```
Lucia Castro (Solo Lectura)
```sql
GRANT SELECT ON tina_cafe.calificaciones TO 'lucia'@'%';
GRANT SELECT ON tina_cafe.envios TO 'lucia'@'%';
GRANT SELECT ON tina_cafe.cliente TO 'lucia'@'%';
GRANT SELECT ON tina_cafe.orden TO 'lucia'@'%';
GRANT SELECT ON tina_cafe.pagos TO 'lucia'@'%';

```
Manuela Baxovanos (Lectura y Escritura Limitada)
```sql
GRANT SELECT, INSERT, UPDATE ON tina_cafe.producto TO 'manuela'@'%';
GRANT SELECT, INSERT, UPDATE ON tina_cafe.categoria_producto TO 'manuela'@'%';
GRANT SELECT, INSERT, UPDATE ON tina_cafe.inventario TO 'manuela'@'%';
GRANT SELECT, INSERT, UPDATE ON tina_cafe.proveedor TO 'manuela'@'%';

```
### Paso 3: Aplicar los cambios
```sql
FLUSH PRIVILEGES;
```
---

# Cómo Consultar los Usuarios y sus Permisos en MySQL

Los privilegios están almacenados en las tablas del sistema, como mysql.user y mysql.db. 
```sql
SELECT 
    user AS 'Usuario',
    host AS 'Host',
    authentication_string AS 'Contraseña',
    Select_priv AS 'SELECT',
    Insert_priv AS 'INSERT',
    Update_priv AS 'UPDATE',
    Delete_priv AS 'DELETE',
    Create_priv AS 'CREATE',
    Drop_priv AS 'DROP',
    Grant_priv AS 'GRANT',
    Index_priv AS 'INDEX',
    Alter_priv AS 'ALTER',
    References_priv AS 'REFERENCES',
    Create_tmp_table_priv AS 'CREATE_TMP_TABLE',
    Lock_tables_priv AS 'LOCK_TABLES',
    Create_view_priv AS 'CREATE_VIEW',
    Show_view_priv AS 'SHOW_VIEW',
    Create_routine_priv AS 'CREATE_ROUTINE',
    Alter_routine_priv AS 'ALTER_ROUTINE',
    Execute_priv AS 'EXECUTE',
    Event_priv AS 'EVENT',
    Trigger_priv AS 'TRIGGER'
FROM 
    mysql.user;
```
