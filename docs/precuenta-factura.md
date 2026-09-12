# Precuenta y reimpresión de factura

La precuenta es un resumen **no fiscal** del pedido que entregas al cliente para
que revise antes de pagar. La factura es el comprobante fiscal que se genera al
cobrar.

## Precuenta

### Generar una precuenta

1. En la pestaña **Caja → Pendientes**, toca **Precuenta** sobre el pedido.
2. La app abre un resumen con:
    - Número de pedido.
    - Fecha.
    - Cliente.
    - Mesa(s).
    - Lista de productos agrupados por nombre y precio (los anulados no
        aparecen).
    - Subtotal.
    - Cargos adicionales.
    - **Propina sugerida** (del porcentaje predeterminado, si está configurado).
    - **TOTAL A PAGAR**.
3. La precuenta se imprime automáticamente (si hay impresora conectada).

![Precuenta](img/precount.png)

!!! note "No fiscal"
    La precuenta **no es una factura**: no tiene número de factura ni datos
    fiscales del establecimiento. Es solo informativo.

### Atajo "Ir a cobrar"

En la parte inferior del modal de precuenta hay un botón **Ir a cobrar**:

1. Pulsa **Ir a cobrar**.
2. La app cierra la precuenta y abre directamente el **modal de transacción**
    con la **propina predeterminada** ya aplicada.
3. Solo queda elegir los métodos de pago y confirmar.

## Factura

La factura se genera **automáticamente** al cobrar un pedido. La app:

1. Crea la transacción.
2. Genera la factura con número correlativo (`INV-yyyyMMdd-XXXXXX`).
3. Si hay datos fiscales activos, los incluye (razón social, NIT, resolución
    DIAN, régimen).
4. Envía el ticket a la impresora configurada.

### Ver la factura

1. En la pestaña **Caja → Historial**, busca el pedido pagado.
2. Toca **Ver factura**.
3. La app muestra la factura con todos los detalles: número, fecha,
    establecimiento, cliente, ítems, cargos, pagos, propina, total y cambio.

![Factura](img/invoice.png)

### Reimprimir la factura

Desde la misma vista de factura, pulsa **Imprimir factura**. La factura se
reimprime en la impresora configurada.

### Cambiar el método de pago de una factura

Solo disponible para **SUPER** y **ADMINISTRADOR**.

1. En la pestaña **Caja → Historial**, toca **Cambiar pago** en la factura.
2. La app abre un modal con el **total bloqueado** (no se puede modificar).
3. Edita los métodos de pago (mismas reglas que al cobrar).
4. Escribe un **motivo del cambio** (opcional, pero recomendado).
5. Pulsa **Guardar**.

!!! warning "Importante"
    El cambio de método de pago se registra en el log de auditoría y deja
    constancia del método anterior.

### Anular una venta pagada

Disponible únicamente para **SUPER** y **ADMINISTRADOR**, y solo cuando el
turno de caja sigue **abierto**.

1. En la pestaña **Caja → Historial**, toca **Anular venta** en la factura.
2. La app abre un modal con la información del pedido y una advertencia.
3. Escribe el **motivo** de la anulación (obligatorio, mínimo 5 caracteres).
4. Pulsa **Anular venta**.

La orden pasa a **Anulada**, se revierte el inventario descontado y la venta
deja de contar en los ingresos de caja del turno. Si el cliente recibió
efectivo, registra su devolución por separado desde **Egresos de caja →
Devolución al cliente**. Detalles completos en
[Anular una venta pagada](anular-venta.md).

### Reenviar la factura por email

Si el cliente quiere recibir la factura por correo:

1. Abre la factura.
2. Pulsa **Enviar por email**.
3. Si la factura tiene un email registrado, se envía.

!!! note "Reintento de envío"
    Si el envío falla (por ejemplo, servidor de email caído), la factura queda en
    estado **FAILED**. El sistema reintenta automáticamente hasta 3 veces.
    Un administrador puede forzar un reintento desde la pantalla de facturas.

## Estados de la factura

| Estado | Significado |
|---|---|
| `PENDING` | Generada pero pendiente de envío. |
| `GENERATED` | Generada localmente y lista para imprimir. |
| `SENT` | Enviada por email al cliente. |
| `FAILED` | Falló el envío por email (reintento automático en curso). |