# Reportes

El módulo **Reportes** permite analizar las ventas y anulaciones de la sucursal
por distintos criterios: rango de fechas, turno, fecha exacta, ventas por
producto, ranking de productos más vendidos y órdenes anuladas.

**Rol requerido:** Administrador. Los cajeros ven solo sus propios turnos.

## Pantalla principal

Menú lateral → **Reportes**.

![Reportes](img/reports.png)

Selecciona primero el **tipo de reporte**:

1. **Por rango de fechas** — agrupa todas las ventas entre dos fechas (día
    completo).
2. **Por fecha-hora exacta** — para turnos nocturnos que cruzan la medianoche.
3. **Por turno específico** — reporte detallado de un turno (necesita su ID).
4. **Por fecha de apertura de turno(s)** — incluye todos los turnos abiertos en
    una fecha.
5. **Ventas por Producto (selección)** — elige los productos a consultar y un
    rango fecha-hora para ver cuántas veces se vendió cada uno.
6. **Top de Productos Vendidos** — ranking de los productos más vendidos en un
    rango de fecha-hora.
7. **Órdenes Anuladas** — ventas pagadas anuladas y cancelaciones pre-pago en
    un rango de fecha-hora, con motivo y auditoría. Ver
    [Órdenes Anuladas](#órdenes-anuladas).

## Configurar el reporte

Una vez elegido el tipo, completa los selectores:

- **Rango de fechas**: desde / hasta.
- **Fecha-hora exacta**: desde / hasta (con hora).
- **Turno específico**: ID del turno (lo encuentras en **Cierres pendientes**
    o **Historial de turnos**).
- **Fecha de apertura**: solo una fecha.
- **Ventas por Producto (selección)**: selecciona los productos en el checklist
    agrupado por categoría/subcategoría y define el rango fecha-hora.
- **Top de Productos Vendidos**: solo el rango fecha-hora (la lista de productos
    la devuelve el sistema).

## Tarjetas de resumen

Al ejecutar el reporte, la app muestra:

- **Transacciones** — número total de transacciones del período.
- **Ventas** — suma total de ventas (sin propinas ni cargos).
- **Propinas** — suma total de propinas.
- **Ingreso bruto** — ventas + propinas.

![Resumen de reporte](img/reports-summary.png)

## Desglose por medios de pago

Una sección muestra, para cada método de pago:

- Número de transacciones.
- Porcentaje del total.
- Monto total.

![Desglose por medios](img/reports-payment-breakdown.png)

## Resumen por cajero

Si el reporte incluye varios turnos, muestra también el detalle por cada cajero:

- Cajero.
- Número de transacciones.
- Ventas.
- Propinas.

![Resumen por cajero](img/reports-by-cashier.png)

## Reporte de un turno específico

Si elegiste "Por turno específico", además de las tarjetas verás la **tarjeta
de información del turno**:

- Número de turno.
- Cajero.
- Terminal.
- Estado (OPEN / CLOSED / RECONCILED).
- Fecha y hora de apertura / cierre.

![Info del turno](img/reports-shift-info.png)

## Ventas por Producto (selección)

### Objetivo

Conocer con qué frecuencia se vendió un producto puntual durante un periodo
determinado. Pensado para auditar productos específicos (un combo nuevo, un
producto estacional, etc.).

### Rol

Administrador.

### Paso a paso

1. Menú lateral → **Reportes**.
2. En el selector de tipo elige **Ventas por Producto (selección)**.
3. La app muestra el catálogo cargado como **checklist agrupado por
    categoría y subcategoría**. Marca uno o varios productos.
    - Cada subcategoría tiene un checkbox propio para seleccionar todos sus
        productos en un solo paso.
    - Hay un botón **Seleccionar todos** en la parte inferior del listado.
    - Existe un botón **Limpiar** para vaciar la selección actual.
4. Define el **rango fecha-hora** (desde / hasta, con hora). El orden de
    selección es fecha → hora inicio → fecha → hora fin.
5. Pulsa **Consultar reporte**.

### Resultado

La app muestra:

- **Resumen del período**: cantidad de productos consultados, unidades
    vendidas e ingreso total.
- **Una tarjeta por producto**, con:
    - **Veces vendido** (número de líneas de venta en que apareció).
    - **Unidades** y **Ingreso**.
- Los **productos que no tuvieron ventas en el período** aparecen listados
    igual, con totales en cero y la etiqueta "Sin ventas en el período".

![Ventas por producto](img/reports-products.png)

## Top de Productos Vendidos

### Objetivo

Identificar los productos más vendidos en un período determinado para tomar
decisiones de menú, promociones o compras de inventario.

### Rol

Administrador.

### Paso a paso

1. Menú lateral → **Reportes**.
2. En el selector de tipo elige **Top de Productos Vendidos**.
3. Define el **rango fecha-hora** (desde / hasta, con hora).
4. Pulsa la consulta — **no requiere seleccionar productos**.

### Resultado

La app muestra:

- **Resumen del período**: total de transacciones, productos distintos
    vendidos, unidades vendidas, ingreso total.
- **Ranking numerado** de los productos con al menos una venta, ordenado por
    **unidades vendidas** de mayor a menor. Cada tarjeta muestra:
    - Posición (los 3 primeros llevan un destacado visual).
    - Nombre del producto y categoría / subcategoría.
    - **Unidades**, **veces vendido** y **%** sobre el total de unidades.
    - **Ingreso** generado por el producto.

!!! warning "Limitación"
    Este reporte muestra solo el ranking agregado (veces vendido, unidades,
    ingreso y porcentaje). Para auditar un producto puntual, usa el reporte
    "Ventas por Producto (selección)" en el mismo período.

![Top de productos](img/reports-top-products.png)

## Órdenes Anuladas

### Objetivo

Auditar quién anula y por qué cada orden (tanto ventas pagadas anuladas como
cancelaciones pre-pago), en un rango de fecha-hora. Permite detectar
patrones de cancelación y conciliar la operación con la caja.

### Rol

Administrador.

### Paso a paso

1. Menú lateral → **Reportes**.
2. En el selector de tipo elige **Órdenes Anuladas**.
3. Define el **rango fecha-hora** (desde / hasta, con hora).
4. Pulsa la consulta.

### Resultado

La app muestra una **tarjeta de resumen** con:

- **Total anuladas** — cantidad de órdenes anuladas en el período.
- **Ventas pagadas anuladas** — transacciones `SALE` canceladas después del pago.
- **Canceladas pre-pago** — órdenes anuladas antes de pagar.
- **Valor total** — suma de los valores anulados.
- **Propinas** — suma de propinas (solo aplica a ventas pagadas).

A continuación, una **tarjeta por cada anulación** con:

- **Número de orden** y un chip de tipo: **Venta pagada** (rojo) o
    **Anulada pre-pago** (naranja).
- **Monto anulado** (en rojo).
- **Motivo** de la anulación.
- **Anulado por** — nombre del usuario que la anuló.
- **Fecha y hora** de la anulación.
- **Mesero**, **Cliente**, **Origen** y (solo ventas pagadas) **Factura**,
    **Turno**, **Cajero**, **Propina**.
- (Solo ventas pagadas) **Desglose de métodos de pago** como chips azules con
    el monto por método.

![Órdenes anuladas](img/reports-annulled-orders.png)

!!! note "Cancelaciones pre-pago sin auditoría"
    Las cancelaciones realizadas **antes** de la versión del sistema que
    registra `cancelledAt` (migración V26_0) no aparecen en el reporte.
    Solo verás cancelaciones que ya cuentan con fecha y motivo capturados.

!!! tip "Caso de uso"
    Si la orden anulada fue una **venta pagada**, el sistema además devolvió el
    inventario descontado y la sacó de los ingresos de caja al momento de la
    anulación (no es necesario hacer ningún ajuste manual en el inventario).
    Si devolviste efectivo al cliente, registra esa salida desde
    **Egresos de caja → Devolución al cliente**.

## Diferenciación por rol

- **Cajero**: solo puede ver reportes de **sus propios turnos** (selector
    "Por turno" está limitado a los turnos donde fue cajero).
- **Administrador**: ve todos los turnos y reportes de la sucursal.

## Tipos de transacciones incluidas

Solo se incluyen en el reporte las transacciones:

- **Tipo**: `SALE` (ventas) y `REFUND` (reembolsos).
- **Estado**: `COMPLETED` (completadas).

Las transacciones canceladas (`CANCELLED`) o pendientes (`PENDING`) **no**
aparecen.

!!! note "Notas para los nuevos reportes"
    - Los reportes **"Ventas por Producto"** y **"Top de Productos Vendidos"**
        usan la misma regla que el resto: solo transacciones `SALE +
        COMPLETED`.
    - Las **líneas de pedido (`OrderDetail`)** en estado `CANCELED` (anuladas)
        se excluyen de estos dos reportes.
    - Las transacciones sin un pedido asociado válido se ignoran en el
        cálculo de ventas por producto.

## Buenas prácticas

- Genera reportes al **final del día** para hacer cierre diario.
- Para auditoría mensual, usa **rango de fechas** con cuidado si tu local opera
    en turnos nocturnos (puede haber ventas del turno de noche que caigan en
    dos días calendario distintos).
- Exporta los datos regularmente y guárdalos en un sistema de respaldo.