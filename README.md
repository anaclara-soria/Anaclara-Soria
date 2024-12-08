# Proyecto Tina Cafe

Cafeteria pet friendly libre de gluten dedicada a ofrecer una experiencia unica en un ambiente calido y moderno con sabores de calidad.

## Problematica

Actualmente, mi cafeteria enfrenta varios problemas en la administracion de sus ventas y pedidos. A raiz del incremento de la demanda, se ha vuelto difícil medir la rentabilidad real del negocio, realizar un correcto seguimiento de ventas, controlar el inventario y actualizar la informacion referida a clientes, ordenes y empleados. Veo necesaria la creacion de un sistema que permita almacenar y manipular toda esta informacion con el objetivo de tenemos mejor visibilidad de los resultados del negocio y tomar decisiones efectivas.

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

Nombre: VARCHAR(200) 

Nombre del producto

Precio: DECIMAL(10,2). Precio del producto. 

id_categoria_producto: int
Referencia a la categoría del producto.

**3) Categoria_producto** 

• Descripción: Define las categorías a las que pertenecen los productos. 

• Campos: 

id_categoria_producto: int (PK, auto_increment) - Identificador único de la categoría.

Nombre_categoria: VARCHAR(200). Nombre de la categoría. 

Descripcion: VARCHAR(200). Descripción de la categoría.

**4) Cliente** 

• Descripción: Almacena información sobre los clientes. 

• Campos: 

id_cliente: int (PK, auto_increment) - Identificador único del cliente. 

Nombre: VARCHAR(200). Nombre del cliente. 

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

**7) Pagos** 

• Descripción: Almacena información sobre los pagos realizados por las órdenes. 

• Campos:

id_pagos: int (PK, auto_increment) - Identificador único del pago.

id_detalle_orden: int - Referencia a los detalles de la orden pagada.

fecha: DATE - Fecha del pago.

**8) Detalle_orden** 

• Descripción: Almacena los detalles de cada orden, incluyendo los productos y cantidades. 

• Campos: 

id_detalle_orden: int (PK, auto_increment) - Identificador único del detalle de la orden.

id_orden: int - Referencia a la orden correspondiente. 

id_producto: int - Referencia al producto en la orden. 

id_empleado: int - Referencia al empleado que gestiona el detalle. 

cantidades: DECIMAL(10,2) - Cantidad del producto en la orden.


## Relaciones

• producto tiene una relación de clave foránea con categoria_producto. 

• orden tiene relaciones de clave foránea con cliente, producto y empleado. 

• pagos tiene una relación de clave foránea con detalle_orden.

• detalle_orden tiene relaciones de clave foránea con orden, producto y empleado. 

• proveedor tiene una relación de clave foránea con producto.

**Problemas que Resuelve:**

*Gestión de Inventario:* Permite llevar un control de los productos por categoría y por proveedor.

*Gestión de Empleados:* Organiza la información del personal y su relación con las órdenes.

*Gestión de Proveedores:* Organiza la información de los proveedores y su relación con cada producto.

*Control de Pagos:* Facilita el seguimiento de los pagos realizados por los clientes.

*Análisis de Ventas:* Permite obtener conclusiones de ventas por producto y categoría permitiendo analizar la tendencia de las mismas y la rentabilidad del negocio. También permite tener mayor control sobra las ventas por empleado y evaluar su rendimiento.

Esta estructura permite un manejo eficiente y organizado de la información del café, facilitando la toma de decisiones y mejorando el servicio al cliente.



## Diagrama Entidad - Relacion

![image](https://github.com/user-attachments/assets/a858b2f7-7f5f-4963-9b14-a7461206a69e)

**Resumen de los Datos Insertados:**

- Categoria_producto: Tres categorías: Bebidas, Comidas y Snacks.

- Producto: Se han añadido cinco productos en tres categorías diferentes.

- Proveedor: Tres proveedores asociados a los productos.

- Cliente: Tres clientes con diferentes correos electrónicos y números de teléfono.

- Empleado: Tres empleados con distintos puestos en el café.

- Orden: Tres órdenes realizadas por tres clientes, cada una asociada con un producto y un empleado.

- Detalle_orden: Tres detalles de orden con las cantidades de los productos comprados.

- Pagos: Tres pagos asociados a las órdenes.

 # Objetos de la base de datos

 ## Vistas aplicadas y Descripciones

*`Vista_Ventas_por_periodo`*: Sumatoria de los precios de los productos vendidos.
   Objetivo: XXX

  **Tablas que componen la vista:** 
- *Orden*: Proporciona la fecha de cada orden.
- *Detalle de orden*: Proporciona las cantidades de cada id de productos por cada id de orden
- *Producto*: Proporciona el precio de cada producto.

*`Vista_Ventas_por_producto`*: Total de unidades vendidas y la suma de ingresos por cada producto con el objetivo de visualizar que productos son mas populares.

 **Tablas que componen la vista:** 

- *Detalle de orden*: Proporciona las cantidades de cada id de productos por cada id de orden
- *Producto*: Proporciona el precio de cada producto.
  
*`Vista_Ventas_por_categoria`*: Total de ventas y unidades por cada categoría de producto (e.g., bebidas, comidas, snacks).

**Tablas que componen la vista:** 

- *Detalle de orden*: Proporciona las cantidades de cada id de productos por cada id de orden
- *Producto*: Proporciona el precio de cada producto.
- *Categoria de producto*: Proporciona el nombre de cada categoria de producto.
  
*`Vista_Ventas_por_empleado`*: Analizar qué empleados están generando más ingresos de acuerdo a las ordenes colocadas

**Tablas que componen la vista:** 

- *Detalle de orden*: Proporciona las cantidades de cada id de productos por cada id de orden
- *Producto*: Proporciona el precio de cada producto.
- *Empleado*: Proporciona el nombre de cada empleado. 

