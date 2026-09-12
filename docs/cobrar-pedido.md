# Cobrar un pedido

La pestaña **Caja** permite registrar el cobro de un pedido finalizado.

**Rol requerido:** Cajero, Administrador.

## Pantalla principal

1. En la barra inferior, toca **Caja**.
2. Verás dos pestañas:
    - **Pendientes** — pedidos en estado **Abierto** o **Finalizado**, listos
        para cobrar.
    - **Historial** — pedidos ya pagados o anulados.

![Pantalla Caja](img/cash-register.png)

### Acciones sobre pedidos pendientes

- **Detalle** — abre el pedido en modo lectura.
- **Pagar** — abre el modal de cobro (ver abajo).
- **Cargos** — gestiona cargos adicionales antes de cobrar.
- **Precuenta** — genera un ticket no fiscal para que el cliente revise.
- **Anular pedido** — cancela el pedido antes de cobrar (ver advertencia).
- **Imprimir precuenta** — reimprime la precuenta en la impresora.

### Acciones sobre pedidos del historial

- **Detalle** — abre el pedido en modo lectura.
- **Ver factura** — muestra la factura generada (también se puede reimprimir).
- **Cambiar pago** — solo `SUPER` y `ADMINISTRADOR`: modifica los métodos de
    pago de una transacción ya cobrada (requiere motivo).
- **Anular venta** — solo `SUPER` y `ADMINISTRADOR`: anula la transacción,
    revierte el inventario descontado y saca la venta de los ingresos de caja
    (requiere motivo). Ver [Anular una venta pagada](anular-venta.md).

## Cobrar un pedido (modal de transacción)

1. En la pestaña **Pendientes**, toca **Pagar** sobre el pedido a cobrar.
2. Se abre un modal con:
    - Resumen del pedido (número, mesa, cliente, total).
    - Selector de **tipo de transacción**: **Venta** o **Reembolso**.
    - Sección de **propina** (ver siguiente).
    - Sección de **pagos** (ver siguiente).
    - Resumen en vivo: total pedido, propina, total a pagar, total cubierto,
        **cambio**.

![Modal de transacción](img/transaction-modal.png)

### Propina

El cajero puede sugerir o ajustar la propina de tres formas equivalentes:

- **Porcentaje** — botones rápidos 0% / 5% / 10% / 15%, o un valor manual.
- **Monto** — un valor en pesos.
- **Total a pagar** — el sistema recalcula la propina implícita.

Los tres campos están sincronizados: si modificas uno, los otros se actualizan
para mantener la coherencia.

!!! tip "Propina predeterminada"
    Puedes guardar tu porcentaje favorito como predeterminado desde el icono de
    **disquete** junto al campo de porcentaje. La próxima vez que abras el
    modal, se cargará automáticamente.

### Métodos de pago

1. En la sección **Pagos**, selecciona el **método** (efectivo, tarjeta de
    crédito, débito, QR, transferencia bancaria, vale).
2. Escribe el **monto**.
3. Repite para agregar más métodos si el cliente paga con varios (pago
    **split**).

#### Pago con tarjeta

Si el método es **Tarjeta de crédito** o **Tarjeta de débito**, la app pide
datos opcionales:

- **Últimos 4 dígitos** — los 4 números al frente de la tarjeta.
- **Franquicia** — Visa, Mastercard, Amex, etc.
- **Código de autorización** — el código que devuelve el datafono.
- **Referencia** — número de voucher o referencia.

![Datos de tarjeta](img/card-fields.png)

!!! note "Privacidad"
    Estos campos son **opcionales** y solo se guardan localmente en la
    transacción. No se almacenan en el servidor de forma sensible.

### Validaciones antes de cobrar

- El **total cubierto** debe ser **mayor o igual** al total a pagar.
- Si el total cubierto es mayor, la diferencia aparece como **cambio a
    devolver** (solo aplica a pagos en efectivo).
- No puedes repetir el mismo método de pago dos veces.

### Confirmar el cobro

1. Verifica los totales.
2. Pulsa **Completar transacción**.
3. La app crea la transacción en el servidor y muestra un modal de éxito con:
    - Número de factura.
    - **Cambio a devolver** (si aplica).
    - Botón **Imprimir factura** para enviar el ticket al cliente.

![Modal de éxito de transacción](img/transaction-success.png)

## Reembolsar una transacción

Si necesitas devolver el dinero de una venta ya cobrada:

1. En la pestaña **Historial**, busca la transacción.
2. Toca **Detalle** y luego **Reembolsar** (o usa la opción desde la pantalla de
    la factura).
3. La app crea una nueva transacción tipo **REFUND** vinculada a la original.

!!! warning "Importante"
    El reembolso queda registrado con el mismo número de factura referenciado y
    requiere rol **SUPER** o **ADMINISTRADOR**.

## Anular un pedido antes de cobrar

Si el pedido se creó por error o el cliente se fue sin consumir:

1. Toca **Anular pedido** en la tarjeta (solo en la pestaña **Pendientes**).
2. Se abre un modal con la información del pedido y una advertencia. Escribe
    el **motivo** de la anulación (obligatorio, mínimo 5 caracteres).
3. Toca **Anular orden** para confirmar.

![Anular pedido](img/cancel-order.png)

!!! warning "Importante"
    - Si ya generaste una factura, no anules la orden desde aquí: en su lugar
        usa **Anular venta** desde la pestaña **Historial** (ver
        [Anular una venta pagada](anular-venta.md)). El sistema te lo impedirá
        con un mensaje claro.
    - La anulación no se puede deshacer. La cancelación queda registrada con
        fecha, usuario y motivo en el reporte de
        [Órdenes Anuladas](reportes.md#órdenes-anuladas).
    - La cancelación pre-pago **no afecta caja ni inventario** porque la orden
        aún no se había cobrado. Si fue tomada por error, vuelve a crear la
        orden.

## Solución de problemas

| Problema | Causa | Solución |
|---|---|---|
| "Total cubierto menor al total a pagar" | La suma de pagos no alcanza | Agrega otro método o aumenta un monto. |
| "No se puede repetir el método" | El mismo método ya está agregado | Quita el pago anterior o usa otro método. |
| "No hay caja abierta" | No abriste turno | Ve a **Opciones de caja → Apertura**. |