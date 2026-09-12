# Anular una venta pagada

Una venta ya pagada puede anularse cuando el cliente desiste del pedido, lo
cambia o se detecta un error en el cobro. La anulación revierte los efectos
de la transacción sobre inventario, caja y auditoría.

**Rol requerido:** `SUPER` o `ADMINISTRADOR`.

## Cuándo anular vs. cuándo reembolhar

- **Anular** una venta pagada es la acción correcta cuando el cliente no recibió
  el producto (cambió de opinión antes de consumirlo, error de digitación,
  duplicado, etc.). Esta acción devuelve el inventario y saca la venta de los
  ingresos de caja.
- **Reembolhar** (disponible desde el modal de cobro, tipo **Reembolso**)
  aplica cuando el cliente ya recibió el producto y se le devuelve dinero. El
  reembolso registra un nuevo egreso sin tocar la transacción original.

## Requisitos

- La orden debe estar en estado **Pagada** y tener una factura asociada
  (botón **Ver factura** visible).
- El turno de caja debe estar **abierto**. Si el turno ya se cerró, primero
  ábrelo de nuevo o comunícate con un supervisor.

## Pasos

1. Ve a la pestaña **Caja → Historial**.
2. Ubica la venta que quieres anular. Solo verás el botón **Anular venta** en
   pedidos **pagados** con factura asociada.
3. Toca **Anular venta** en la tarjeta del pedido.
4. Se abre un modal con la información del pedido y una advertencia. Escribe
   el **motivo** de la anulación (obligatorio, mínimo 5 caracteres).
5. Toca **Anular venta** para confirmar.

![Modal de anulación de venta](img/anular-venta.png)

## Qué sucede al anular

| Aspecto | Comportamiento |
|---|---|
| Estado de la orden | Pasa de **Pagada** a **Anulada** |
| Inventario | Los movimientos `SALE` generados al cobrar se revierten; se crea un movimiento `SALE_REVERSAL` por cada insumo descontado, con la cantidad devuelta y la referencia a la orden |
| Ingresos de caja | La venta deja de contar en el arqueo del turno, en el resumen por método de pago y en los reportes de ventas del día |
| Devolución de efectivo | **No es automática.** Si el cliente recibió dinero en efectivo, registra la devolución desde **Egresos de caja** con el motivo **Devolución al cliente** |
| Cambio de método de pago | Queda deshabilitado (la orden ya no es modificable) |
| Reimpresión de factura | Se reemplaza por la vista de detalle con estado Anulada |
| Auditoría | Se registra quién anuló, cuándo y el motivo; los movimientos de inventario reverso quedan firmados por el mismo usuario |

!!! warning "Acción irreversible"
    Una vez anulada, la orden no puede volver a estado **Pagada**. Si el
    cliente cambió de opinión después de anular, registra un **nuevo pedido**.

!!! danger "Solo turno abierto"
    Si el turno de caja ya se cerró, la anulación se rechaza para evitar
    descuadres en el arqueo. Ábrelo de nuevo o contacta al supervisor antes
    de continuar.

!!! tip "Devolución de efectivo al cliente"
    Si el cliente pagó en efectivo, recuerda registrar la devolución en
    **Egresos de caja → Devolución al cliente** con el monto exacto entregado
    al cliente. La anulación de la venta no genera este egreso
    automáticamente.
