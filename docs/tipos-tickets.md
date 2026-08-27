# Tipos de tickets

Restic genera distintos tipos de tickets según el momento. Aquí se explica
qué incluye cada uno y cuándo se imprime.

**Rol requerido:** Cualquier usuario que use la app (las impresiones son
automáticas).

## Resumen de tickets

| Tipo | Cuándo se genera | Para qué sirve |
|---|---|---|
| **Comanda** | Al crear/confirmar un pedido o agregar productos. | Indicar a cocina qué preparar. |
| **Precuenta** | Al pulsar "Precuenta" desde Caja. | Mostrar al cliente cuánto va a pagar. |
| **Factura** | Al cobrar un pedido (transacción SALE completada). | Comprobante fiscal / no fiscal del pago. |
| **Comanda de domicilio** | Al crear un pedido de tipo **Domicilio**. | Comanda específica para entrega a domicilio. |
| **Productos agregados** | Al agregar productos a un pedido existente. | Informar a cocina de los nuevos items. |

## Comanda

Es el ticket que cocina recibe para empezar a preparar.

### Cuándo se imprime

- Al **confirmar un pedido nuevo**.
- Al **agregar productos** a un pedido existente (solo los ítems nuevos).

### Qué incluye

- Número de pedido.
- Tipo (Salón / Para llevar / Domicilio).
- Mesa(s) o cliente.
- Fecha y hora.
- Lista de ítems con cantidad y notas individuales.
- Observaciones generales del pedido (si existen).
- **Zona de impresión** según la categoría del producto.

![Comanda de cocina](img/ticket-comanda.png)

!!! note "Multi-impresora"
    Los ítems se enrutan automáticamente a la impresora correspondiente según
    la categoría y la zona configurada. Por ejemplo, una pizza va a
    "Cocina-Caliente" y un trago a "Barra".

## Precuenta

Es un resumen **no fiscal** del pedido para que el cliente revise antes de
pagar.

### Cuándo se imprime

- Al pulsar **Precuenta** en la pantalla de Caja.
- Se puede reimprimir en cualquier momento.

### Qué incluye

- Número de pedido.
- Fecha.
- Cliente.
- Mesa(s).
- Lista de ítems (los anulados no aparecen).
- Subtotal.
- Cargos adicionales.
- **Propina sugerida** (calculada con el porcentaje predeterminado).
- **TOTAL A PAGAR**.

![Precuenta](img/ticket-precount.png)

!!! warning "No fiscal"
    La precuenta **no es una factura**. No incluye número de factura ni datos
    fiscales. Solo sirve para revisión del cliente.

## Factura

Es el comprobante que se emite al cobrar un pedido.

### Cuándo se imprime

- Inmediatamente después de **completar una transacción SALE**.
- Se puede **reimprimir** desde la pantalla de factura.

### Qué incluye

- **Encabezado**: datos del establecimiento (razón social, NIT, régimen,
    resolución DIAN, rango de numeración).
- **Número de factura**: `INV-{yyyyMMdd}-{6 dígitos}`.
- Fecha y hora.
- Datos del cliente (si se proporcionaron).
- Lista de ítems con cantidad y precio.
- Cargos adicionales.
- Subtotal.
- Propina.
- **TOTAL**.
- Métodos de pago (con desglose de tarjeta si aplica).
- **Cambio devuelto** (si hubo).
- Información del cajero y del turno.

![Factura](img/ticket-factura.png)

!!! info "Factura electrónica"
    Si tienes **datos fiscales activos**, la factura incluye todos los campos
    requeridos por la DIAN. El sistema genera además un XML interno (visible
    en la base de datos; el envío a la DIAN depende de tu proveedor).

## Comanda de domicilio

Es una variante de la comanda normal que se imprime al crear un pedido tipo
**Domicilio**.

### Qué incluye (adicional a la comanda normal)

- **Dirección de entrega**.
- **Teléfono del cliente**.
- Cualquier nota específica del domicilio (por ejemplo, "Tocar el timbre 2B").

## Productos agregados

Cuando se agregan productos a un pedido ya existente, se imprime un ticket
adicional solo con los **ítems nuevos**.

### Qué incluye

- Número de pedido (mismo).
- Indicación "PRODUCTOS AGREGADOS".
- Lista de ítems nuevos con cantidad y notas.

![Productos agregados](img/ticket-added.png)

!!! tip "Útil para cocina"
    Este ticket evita reimprimir toda la comanda cuando solo se agregan
    productos; cocina ve solo lo que necesita preparar adicionalmente.

## Tamaños de papel

Todos los tipos de tickets están disponibles en **58 mm** y **80 mm**. El
layout se ajusta automáticamente al tamaño configurado (ver
[Configurar la impresora](impresora-configuracion.md)).