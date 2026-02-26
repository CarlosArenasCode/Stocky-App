# Product Vision Statement: Stocky-App
---
**Proyecto:** Stocky-App  
**Fecha:** 24 de Febrero de 2026  
**Autor:** Carlos Arenas  

---

## 🎯 Definición del Alcance Inicial (MVP)

Basado en nuestra visión, el Producto Mínimo Viable (MVP) incluye únicamente las funcionalidades esenciales que resuelven el problema central sin distracciones. A continuación, el alcance para la primera versión:

### 📦 Módulos del MVP

#### 1. Gestión de Usuarios y Autenticación
* Registro e inicio de sesión seguros (con JWT y hashing de contraseñas).
* Perfil de usuario básico.

#### 2. Gestión de Productos (Inventario)
* **CRUD completo:** Crear, ver, editar y eliminar (o desactivar) productos.
* **Campos requeridos:** Nombre, descripción, precio de venta, cantidad en stock, stock mínimo (para alertas).
* Listado de productos con búsqueda por nombre.
* Visualización de alerta de stock bajo (cuando la cantidad sea menor o igual al stock mínimo).

#### 3. Gestión de Clientes
* **CRUD básico de clientes:** Nombre, teléfono, email (opcional).

#### 4. Punto de Venta (Registro de Ventas)
* Interfaz simple para buscar productos y agregarlos a un carrito de compras.
* Visualización del total de la venta en tiempo real.
* Posibilidad de seleccionar un cliente (o vender como "consumidor final").
* **Al finalizar la venta:**
  * Se registra la venta con fecha, total, cliente y detalles de los productos vendidos.
  * Se descuenta automáticamente la cantidad vendida del inventario.

#### 5. Reportes Básicos
* Reporte de ventas del día (total y lista de ventas).
* Listado de productos con stock bajo.

---

### 🚫 Fuera del MVP (Para futuras versiones)

* Gestión de múltiples usuarios con roles (empleados vs. dueño).
* Módulo de compras a proveedores.
* Reportes gráficos avanzados (ventas por mes, productos más rentables).
* Facturación electrónica o generación de comprobantes fiscales.