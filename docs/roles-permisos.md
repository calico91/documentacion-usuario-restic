# Roles y permisos

Restic distingue **5 roles** principales. Tu rol determina qué pantallas ves y
qué acciones puedes realizar.

## Roles disponibles

| Rol | Abreviatura | Función principal |
|---|---|---|
| **Superadministrador** | `SUPER` | Acceso total a todas las funciones y módulos del sistema. |
| **Administrador** | `ADMINISTRADOR` | Administra una o varias sucursales: menú, usuarios, inventario, reportes. |
| **Mesero** | `MESERO` | Toma pedidos y atiende mesas. |
| **Cocinero** | `COCINERO` | Visualiza comandas y avanza el estado de los productos en cocina. |
| **Cajero** | `CAJERO` | Opera la caja: apertura, cobros, egresos y cierre de turno. |

## ¿Qué puede hacer cada rol?

Esta tabla resume las **acciones disponibles** por rol. La columna *"Visibilidad
de pantallas"* describe los módulos del menú principal a los que puedes acceder.

| Módulo | SUPER | ADMINISTRADOR | MESERO | COCINERO | CAJERO |
|---|:---:|:---:|:---:|:---:|:---:|
| **Pedidos** (lista y consulta) | ✅ | ✅ | ✅ | | ✅ |
| **Tomar pedido** | ✅ | ✅ | ✅ | | |
| **Comandas** (cocina) | ✅ | ✅ | | ✅ | |
| **Caja** (cobrar pedidos) | ✅ | ✅ | | | ✅ |
| **Caja** (anular venta pagada) | ✅ | ✅ | | | |
| **Opciones de caja** (apertura, cierre, egresos) | ✅ | ✅ | | | ✅ |
| **Cierres pendientes** (conciliar) | ✅ | ✅ | | | |
| **Historial de egresos** | ✅ | ✅ | | | parcial¹ |
| **Menú** | ✅ | ✅ | | ✅ | |
| **Mesas** | ✅ | ✅ | ✅ | | |
| **Clientes** | ✅ | ✅ | ✅ | | ✅ |
| **Usuarios** | ✅ | ✅ | | | |
| **Métodos de pago** | ✅ | ✅ | | | |
| **Inventario** | ✅ | ✅ | | | |
| **Datos fiscales** | ✅ | ✅ | | | |
| **Reportes** | ✅ | ✅ | | | |
| **Configuración de impresora** | ✅ | ✅ | ✅ | | ✅ |
| **Zonas de impresión** | ✅ | ✅ | | | ✅ |

¹ Los cajeros ven **solo sus propios turnos y egresos** en el historial.

## Permisos especiales

Además de la visibilidad por módulo, hay acciones puntuales que solo ciertos roles
pueden ejecutar:

- **Restablecer contraseña de un usuario**: usuarios con módulo `USUARIOS`.
- **Activar/desactivar usuarios**: usuarios con módulo `USUARIOS`.
- **Conciliar un cierre de caja**: solo `SUPER` y `ADMINISTRADOR`.
- **Cambiar el método de pago** de una transacción ya cobrada: solo `SUPER` y
  `ADMINISTRADOR`.
- **Editar el menú, inventario y usuarios**: solo `SUPER` y `ADMINISTRADOR`.
- **Gestionar zonas de impresión y asignar categorías**: solo `SUPER`,
  `ADMINISTRADOR` y `CAJERO`.
- **Configurar el filtro "Solo ver mis pedidos"** (en *Configuración → Ajustes
  de Pedidos*): solo `SUPER` y `ADMINISTRADOR` configuran este flag por
  sucursal.

!!! tip "Consejo"
    Si no ves una opción que crees que deberías tener, consulta con el
    administrador de tu sucursal. El rol y los módulos asignados se definen al
    crear o editar el usuario.