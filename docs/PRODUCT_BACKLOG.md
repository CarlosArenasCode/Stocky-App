# Product Backlog: Stocky-App
---
**Proyecto:** Stocky-App  
**Fecha:** 26 de Febrero de 2026  
**Autor:** Carlos Arenas  

---

## Backlog (Historias de Usuario)
 
| ID | Prioridad (MoSCoW) | Épica | Historia de Usuario | Criterios de Aceptación | Estimación (SP) | Dependencias |
|---|---|---|---|---|---|---|
| HU-001 | Must | Autenticación | **Como** dueño de un pequeño comercio, **quiero** registrarme en el sistema con mi correo y contraseña **para** acceder de forma segura. | • El formulario de registro solicita: nombre, email, contraseña y confirmación.<br>• La contraseña se almacena hasheada (bcrypt).<br>• Se valida que el email no esté registrado previamente.<br>• Al registrarse, se crea el usuario y se redirige al login o se inicia sesión automáticamente. | 3 | Ninguna |
| HU-002 | Must | Autenticación | **Como** usuario registrado, **quiero** iniciar sesión con mi email y contraseña **para** acceder al sistema. | • Formulario de login con email y contraseña.<br>• Validación de credenciales.<br>• Al éxito, se devuelve un token JWT que se almacena en el frontend (localStorage o cookie segura).<br>• Si falla, mensaje de error claro. | 3 | HU-001 |
| HU-003 | Must | Autenticación | **Como** usuario autenticado, **quiero** cerrar sesión **para** salir del sistema de forma segura. | • Botón de cerrar sesión que elimina el token del frontend.<br>• Redirige a la página de login. | 1 | HU-002 |
| HU-004 | Must | Gestión de Productos | **Como** dueño, **quiero** agregar un nuevo producto con nombre, descripción, precio, stock inicial y stock mínimo **para** empezar a gestionar mi inventario. | • Formulario con campos: nombre (obligatorio), descripción (opcional), precio (obligatorio, >0), stock (obligatorio, entero >=0), stock mínimo (opcional, entero >=0, por defecto 0).<br>• Al guardar, se crea el producto en la BD.<br>• Se muestra mensaje de éxito y redirige al listado de productos. | 3 | HU-002 (requiere login) |
| HU-005 | Must | Gestión de Productos | **Como** dueño, **quiero** ver la lista completa de mis productos con su stock actual **para** tener una visión general. | • Tabla o lista que muestre: nombre, precio, stock actual, stock mínimo.<br>• Posibilidad de ordenar por nombre o stock.<br>• Si hay productos con stock <= stock mínimo, se resaltan (alerta). | 2 | HU-004 |
| HU-006 | Must | Gestión de Productos | **Como** dueño, **quiero** editar la información de un producto existente **para** mantener los datos actualizados. | • Desde el listado, un botón “Editar” que lleva a un formulario precargado.<br>• Se pueden modificar todos los campos excepto quizás el ID.<br>• Al guardar, se actualiza el producto.<br>• Validaciones similares al crear. | 2 | HU-004, HU-005 |
| HU-007 | Should | Gestión de Productos | **Como** dueño, **quiero** eliminar un producto (o desactivarlo) **para** que no aparezca en el listado activo pero se mantenga el histórico de ventas. | • Al eliminar, se marca como inactivo (borrado lógico) en lugar de borrado físico.<br>• Los productos inactivos no aparecen en el listado principal, pero podrían verse en una sección aparte.<br>• Confirmación antes de eliminar. | 2 | HU-005 |
| HU-008 | Must | Gestión de Productos | **Como** dueño, **quiero** buscar productos por nombre **para** encontrarlos rápidamente. | • Campo de búsqueda en el listado que filtre los productos a medida que se escribe (o con un botón).<br>• La búsqueda debe ser insensible a mayúsculas y acentos (o al menos simple). | 2 | HU-005 |
| HU-009 | Must | Gestión de Clientes | **Como** dueño, **quiero** registrar un cliente con nombre, teléfono y email **para** asociarlo a futuras ventas. | • Formulario con nombre (obligatorio), teléfono (opcional), email (opcional, con validación de formato si se ingresa).<br>• Se guarda en la BD. | 2 | HU-002 |
| HU-010 | Should | Gestión de Clientes | **Como** dueño, **quiero** ver la lista de clientes registrados y poder editarlos o eliminarlos (borrado lógico) **para** mantener la base de clientes actualizada sin perder histórico. | • Listado similar al de productos con opciones de editar y eliminar.<br>• Borrado lógico para no perder histórico. | 3 | HU-009 |
| HU-011 | Must | Punto de Venta | **Como** empleado/dueño, **quiero** realizar una venta seleccionando productos y cantidades **para** agilizar el cobro. | • Interfaz de punto de venta con: buscador de productos, lista de productos agregados (carrito), cantidad, precio unitario, subtotal.<br>• Al buscar y seleccionar un producto, se agrega al carrito.<br>• Se puede modificar la cantidad.<br>• Se muestra el total acumulado.<br>• Al finalizar, se pide confirmar y se registra la venta. | 8 | HU-004 (productos existentes), HU-002 |
| HU-012 | Must | Punto de Venta | **Como** dueño, **quiero** que al finalizar una venta el stock se descuente automáticamente **para** mantener el inventario actualizado. | • Al confirmar la venta, se reduce la cantidad de cada producto en el inventario.<br>• Si un producto no tiene suficiente stock, se debe impedir la venta o advertir.<br>• Se registra la venta con fecha, total, y detalles de productos vendidos. | 3 | HU-011 |
| HU-013 | Should | Punto de Venta | **Como** dueño, **quiero** poder seleccionar un cliente (o “consumidor final”) **para** asociarlo a la venta. | • En el punto de venta, un selector de clientes (desplegable) con los clientes registrados, más una opción “Consumidor final”.<br>• Al finalizar, la venta queda asociada al cliente seleccionado. | 2 | HU-009, HU-011 |
| HU-014 | Could | Punto de Venta | **Como** dueño, **quiero** aplicar un descuento porcentual o en valor **para** ajustar el total de la venta cuando sea necesario. | • Campo en el punto de venta para ingresar descuento (porcentaje o monto fijo).<br>• El total se recalcula en consecuencia.<br>• El descuento se guarda en el registro de venta. | 2 | HU-011 |
| HU-015 | Must | Reportes | **Como** dueño, **quiero** ver un reporte de las ventas del día **para** saber cuánto he vendido. | • Página de reportes con un resumen: total de ventas del día, número de ventas, y lista de ventas con detalles (hora, total, cliente).<br>• Por defecto muestra el día actual. | 3 | HU-012 |
| HU-016 | Should | Reportes | **Como** dueño, **quiero** ver los productos con stock bajo **para** saber qué debo reponer. | • Lista de productos cuyo stock actual es menor o igual al stock mínimo.<br>• Acceso rápido desde el menú o dashboard. | 1 | HU-005 |
| HU-017 | Could | Reportes | **Como** dueño, **quiero** ver los productos más vendidos en un período **para** enfocar mis compras. | • Gráfico o tabla con los productos más vendidos (por cantidad) en un rango de fechas. | 3 | HU-012 |
| HU-018 | Won't | Usuarios y Roles | **Como** dueño, **quiero** crear usuarios con permisos limitados **para** que mis empleados solo registren ventas sin acceder a reportes o configuración. | • Pantalla de gestión de usuarios con roles.<br>• Al iniciar sesión, se restringen las funcionalidades según el rol. | 8 | HU-002, HU-001 (post-MVP) |
| HU-019 | Won't | Compras | **Como** dueño, **quiero** registrar compras a proveedores **para** aumentar el stock. | • Módulo de compras que permita ingresar productos y cantidades, actualizando el stock. | 5 | HU-004 (post-MVP) |

---

## Requisitos No Funcionales (NFR)

> Estos requisitos no representan funcionalidades de usuario sino atributos de calidad del sistema. Se incorporan directamente en los Criterios de Aceptación globales y en la Definition of Done, y aplican a **todas** las historias.

| ID | Categoría | Descripción | Criterio de cumplimiento |
|---|---|---|---|
| NFR-001 | Usabilidad / Responsividad | Toda pantalla o vista del sistema debe ser responsive (adaptable a tablet y móvil). | El layout se verifica en viewport mobile (≤768 px) y tablet (≤1024 px). Se usa CSS con media queries, Bootstrap o Tailwind. No hay desbordamientos horizontales ni elementos inutilizables en pantallas pequeñas. |
| NFR-002 | Seguridad | Las contraseñas nunca se almacenan en texto plano. | Se usa bcrypt u otro algoritmo de hashing con sal. Validado en HU-001. |
| NFR-003 | Seguridad | No se exponen secretos (API keys, tokens, passwords) en el repositorio. | Revisión en cada PR; secrets gestionados con variables de entorno (.env excluido de git). |
| NFR-004 | Mantenibilidad | El código sigue las convenciones de estilo del proyecto. | Linter y formatter pasan sin errores en cada PR (ESLint / Prettier o equivalente). |
