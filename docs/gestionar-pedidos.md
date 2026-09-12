# Gestionar pedidos abiertos

Además de crear pedidos, puedes consultar, modificar, agregar productos, anular
ítems parciales y anular pedidos completos.

**Rol requerido:** Mesero, Cajero (consulta), Administrador (anulación).

## Pantalla Pedidos

1. Desde la barra inferior, toca **Pedidos**.
2. La pantalla muestra dos pestañas:
    - **Activos** — pedidos en estado **Abierto** (OPEN).
    - **Finalizados** — pedidos en estado **Finalizado** (FINALIZED, listos
        para cobrar).

![Pantalla Pedidos](img/orders-list.png)

### Navegación por fecha

- En la parte superior hay un selector de fecha con flechas ◀ ▶.
- Puedes moverte entre días (la app no permite fechas futuras).
- Por defecto muestra el día actual.

### Búsqueda

El campo de búsqueda filtra por:

- Número de pedido.
- Nombre o apellido del cliente.
- Número o nombre de mesa.

### Tarjeta de pedido

Cada tarjeta muestra:

- Número de pedido.
- Tipo: **Salón**, **Para llevar**, **Domicilio**.
- Estado con chip de color.
- Total a pagar.
- Cliente.
- Mesero que lo creó.
- Mesa(s) (si es salón).
- Fecha y hora.

Las acciones disponibles en cada tarjeta dependen del estado:

| Acción | Activos | Finalizados |
|---|:---:|:---:|
| **Ver detalle** | ✅ | ✅ |
| **Agregar productos** | ✅ | ✅ |
| **Cargos** (gestionar recargos) | ✅ | ✅ |
| **Imprimir comanda** (cocina) | ✅ | ✅ |
| **Imprimir precuenta** | ✅ | ✅ |
| **Anular pedido** | ✅ | ✅ |

## Ver el detalle de un pedido

1. Toca la tarjeta del pedido.
3. Se abre un modal con toda la información: items, notas, cargos, subtotal,
    total y estado.

![Detalle de pedido](img/order-detail.png)

## Avanzar el estado de los ítems (servido / anulado)

1. En el modal de detalle, selecciona los ítems que quieres marcar.
2. Elige el nuevo estado:
    - **Servido** — entregado al cliente.
    - **Anulado** — no se entregó y se descuenta del total.
3. Pulsa **Confirmar**.

### Anulación parcial

Si un ítem tiene **cantidad mayor a 1** y marcas "Anulado", la app te preguntará
cuántas unidades anular. Por ejemplo, si pediste 3 hamburguesas y solo anulas 1,
la app deja 1 anulada y 2 activas.

![Anulación parcial](img/partial-cancel.png)

## Agregar productos a un pedido existente

1. Toca el pedido → **Agregar productos** (o el ícono `+` en el modal).
2. La app abre el catálogo en un modal con las mismas funciones que al tomar un
    pedido.
3. Selecciona productos, cantidades, notas y combos.
4. Pulsa **Agregar al pedido**.

!!! note "Reabrir un pedido finalizado"
    Si el pedido está en estado **FINALIZED**, la app permite agregar productos
    y vuelve a ponerlo en **OPEN** automáticamente.

## Imprimir comanda o precuenta

Desde la tarjeta del pedido o desde el detalle:

- **Imprimir comanda** — envía la comanda a las impresoras de cocina (rutas por
    categoría/zona).
- **Imprimir precuenta** — genera un ticket no fiscal con el resumen para que el
    cliente revise antes de pagar.

## Anular un pedido completo

Disponible para **SUPER**, **ADMINISTRADOR**, **MESERO** y **CAJERO**
(solo pedidos abiertos sin pago).

1. Toca la tarjeta del pedido → **Anular pedido** (si está visible).
2. Se abre un modal con la información del pedido y una advertencia. Escribe
    el **motivo** de la anulación (obligatorio, mínimo 5 caracteres).
3. Toca **Anular orden** para confirmar.

!!! warning "Importante"
    - Anular un pedido lo deja en estado **CANCELED` y no se puede deshacer.
    - La cancelación queda registrada con fecha, usuario y motivo en el reporte
        de [Órdenes Anuladas](reportes.md#órdenes-anuladas).
    - Si el pedido ya tiene una transacción pagada, el sistema no te dejará
        anularlo desde aquí: usa **Anular venta** desde la pestaña **Historial**
        de Caja (ver [Anular una venta pagada](anular-venta.md)).
    - La cancelación pre-pago **no descuenta inventario** porque el inventario
        solo se descuenta al cobrar. Si fue tomada por error, vuelve a crear
        el pedido.

## Filtro "Solo ver mis pedidos" (meseros)

Este filtro hace que la lista de **Pedidos** y de **Caja** muestre únicamente los
pedidos que creó el mesero que está usando la app. Aplica a toda la sucursal
y lo configura el administrador.

**Rol requerido:** Administrador o Super (para configurarlo).

1. Abre el menú lateral y toca **Configuración** para expandirla.
2. Toca **Ajustes de Pedidos**.
3. Activa el interruptor **"Solo ver mis pedidos (meseros)"**.
4. Vuelve al menú lateral; el cambio ya está aplicado en la sucursal.

![Pantalla Ajustes de Pedidos](img/order-settings.png)

!!! tip "Consejo"
    Si un mesero ve pedidos de todos los compañeros y quieres que solo vea los
    suyos, entra a **Ajustes de Pedidos** y activa el interruptor. El efecto es
    inmediato: al refrescar, los meseros verán únicamente los pedidos que ellos
    mismos crearon.