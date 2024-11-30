PROBLEMATICA:
Sistema de administracion de “Tina Café”. 
Necesidad de  un sistema para llevar a cabo un control de pedidos, inventarios, la información de cada cliente y empleado.

TABLAS:
1) Proveedor
•	Descripción: Almacena información sobre los proveedores de productos.
•	Campos:
o	id_proveedor: int (PK, auto_increment) - Identificador único del proveedor.
o	id_producto: int - Referencia al producto que proporciona.
o	nombre: VARCHAR(200) - Nombre del proveedor.
o	telefono: VARCHAR(200) - Número de teléfono del proveedor.
o	direccion: VARCHAR(200) - Dirección del proveedor.
o	email: VARCHAR(200) (UNIQUE) - Correo electrónico del proveedor.

2) Producto
•	Descripción: Almacena información sobre los productos ofrecidos en el café.
•	Campos:
o	id_producto: int (PK, auto_increment) - Identificador único del producto.
o	nombre: VARCHAR(200) - Nombre del producto.
o	precio: DECIMAL(10,2) - Precio del producto.
o	id_categoria_producto: int - Referencia a la categoría del producto.

3) categoria_producto
•	Descripción: Define las categorías a las que pertenecen los productos.
•	Campos:
o	id_categoria_producto: int (PK, auto_increment) - Identificador único de la categoría.
o	nombre_categoria: VARCHAR(200) - Nombre de la categoría.
o	descripcion: VARCHAR(200) - Descripción de la categoría.

4) Cliente
•	Descripción: Almacena información sobre los clientes.
•	Campos:
o	id_cliente: int (PK, auto_increment) - Identificador único del cliente.
o	nombre: VARCHAR(200) - Nombre del cliente.
o	email: VARCHAR(200) (UNIQUE) - Correo electrónico del cliente.
o	telefono: VARCHAR(200) - Número de teléfono del cliente.


5) Empleado
•	Descripción: Almacena información sobre los empleados del café.
•	Campos:
o	id_empleado: int (PK, auto_increment) - Identificador único del empleado.
o	nombre: VARCHAR(200) - Nombre del empleado.
o	direccion: VARCHAR(200) - Dirección del empleado.
o	email: VARCHAR(200) (UNIQUE) - Correo electrónico del empleado.
o	telefono: VARCHAR(100) - Número de teléfono del empleado.
o	puesto: VARCHAR(200) - Puesto de trabajo del empleado.

6) Orden
•	Descripción: Almacena información sobre las órdenes realizadas por los clientes.
•	Campos:
o	id_orden: int (PK, auto_increment) - Identificador único de la orden.
o	id_cliente: int - Referencia al cliente que realiza la orden.
o	id_producto: int - Referencia al producto ordenado.
o	id_empleado: int - Referencia al empleado que gestiona la orden.
o	fecha: DATE - Fecha en que se realizó la orden.

7) Pagos
•	Descripción: Almacena información sobre los pagos realizados por las órdenes.
•	Campos:
o	id_pagos: int (PK, auto_increment) - Identificador único del pago.
o	id_detalle_orden: int - Referencia a los detalles de la orden pagada.
o	fecha: DATE - Fecha del pago.

8) Detalle_orden
•	Descripción: Almacena los detalles de cada orden, incluyendo los productos y cantidades.
•	Campos:
o	id_detalle_orden: int (PK, auto_increment) - Identificador único del detalle de la orden.
o	id_orden: int - Referencia a la orden correspondiente.
o	id_producto: int - Referencia al producto en la orden.
o	id_empleado: int - Referencia al empleado que gestiona el detalle.
o	cantidades: DECIMAL(10,2) - Cantidad del producto en la orden.

Relaciones:

•	producto tiene una relación de clave foránea con categoria_producto.
•	orden tiene relaciones de clave foránea con cliente, producto y empleado.
•	pagos tiene una relación de clave foránea con detalle_orden.
•	detalle_orden tiene relaciones de clave foránea con orden, producto y empleado.
•	proveedor tiene una relación de clave foránea con producto.

Problemas que Resuelve:
1.	Gestión de Inventario: Permite llevar un control de los productos por categoría y por proveedor.

2.	Gestión de Empleados: Organiza la información del personal y su relación con las órdenes.

3.	Gestión de Proveedores: Organiza la información de los proveedores y su relación con cada producto.

4.	Control de Pagos: Facilita el seguimiento de los pagos realizados por los clientes.

5.	Análisis de Ventas: Permite obtener conclusiones de ventas por producto y categoría permitiendo analizar la tendencia de las mismas y la rentabilidad del negocio. También permite tener mayor control sobra las ventas por empleado y evaluar su rendimiento.

Esta estructura permite un manejo eficiente y organizado de la información del café, facilitando la toma de decisiones y mejorando el servicio al cliente.


DIAGRAMA ENTIDAD-RELACION (DER)

![image](https://github.com/user-attachments/assets/a858b2f7-7f5f-4963-9b14-a7461206a69e)

Resumen de los Datos Insertados:

- categoria_producto: Tres categorías: Bebidas, Comidas y Snacks.
- producto: Se han añadido cinco productos en tres categorías diferentes.
- proveedor: Tres proveedores asociados a los productos.
- cliente: Tres clientes con diferentes correos electrónicos y números de teléfono.
- empleado: Tres empleados con distintos puestos en el café.
- orden: Tres órdenes realizadas por tres clientes, cada una asociada con un producto y un empleado.
- detalle_orden: Tres detalles de orden con las cantidades de los productos comprados.
- pagos: Tres pagos asociados a las órdenes.
