# Inventario

El módulo **Inventario** gestiona los **insumos** (materias primas, productos
terminados) y sus **movimientos** (entradas, salidas, ajustes).

**Rol requerido:** Administrador.

## Pantalla principal

Menú lateral → **Inventario**.

![Inventario](img/inventory.png)

Tiene tres pestañas:

- **Insumos** — alta, edición y listado de los productos físicos.
- **Movimientos** — entradas, salidas y ajustes de stock.
- **Alertas** — insumos con stock bajo el mínimo.

## Pestaña Insumos

### Crear un insumo

1. En la pestaña **Insumos**, pulsa el botón **+**.
2. Completa el formulario:
    - **Nombre** (obligatorio).
    - **Unidad** — selecciona de la lista:
        - `KG` (kilogramo)
        - `G` (gramo)
        - `L` (litro)
        - `ML` (mililitro)
        - `UNIT` (unidad)
        - `CAJA` (caja)
        - `DOCENA` (docena)
    - **Stock actual** (puede ser 0).
    - **Stock mínimo** — umbral para alertas.
3. Pulsa **Guardar**.

![Formulario de insumo](img/inventory-item-form.png)

### Ver productos asociados

Para cada insumo puedes ver la lista de **productos** que lo usan (a través de
las recetas):

1. Toca el insumo.
2. Pulsa **Ver productos asociados**.

![Productos asociados](img/item-products.png)

### Exportar a CSV

1. En la pestaña **Insumos**, pulsa **Exportar CSV**.
2. La app genera un archivo con todos los insumos: nombre, unidad, stock actual,
    stock mínimo, estado (OK / BAJO / SIN STOCK).
3. Elige con qué app abrirlo.

### Eliminar un insumo

1. Toca el insumo → **Eliminar** (icono papelera).
2. Confirma.

!!! warning "Importante"
    - La eliminación es **lógica** (el insumo se desactiva). No se borra del
        historial de movimientos.
    - Un insumo con recetas asociadas o movimientos recientes puede no ser
        eliminable; desactívalo en su lugar.

## Pestaña Movimientos

### Tipos de movimiento

| Tipo | Código | Descripción |
|---|---|---|
| Compra | `PURCHASE` | Entrada por compra a proveedor. |
| Venta | `SALE` | Descuento automático al cobrar una venta. |
| Ajuste positivo | `ADJUSTMENT_POSITIVE` | Sumar stock (corrección manual). |
| Ajuste negativo | `ADJUSTMENT_NEGATIVE` | Restar stock (corrección manual). |
| Merma | `WASTE` | Pérdida por vencimiento, daño, etc. |
| Inicial | `INITIAL` | Stock inicial al cargar el sistema. |

### Crear un movimiento manual

1. En la pestaña **Movimientos**, pulsa el botón **+**.
2. Completa:
    - **Insumo** — selecciona de la lista.
    - **Tipo** — `PURCHASE`, `ADJUSTMENT_POSITIVE`, `ADJUSTMENT_NEGATIVE`,
        `WASTE` o `INITIAL` (no se permite crear movimientos tipo `SALE`
        manualmente).
    - **Cantidad** — en la unidad del insumo.
    - **Notas** (opcional; por ejemplo, "Factura 1234 de Proveedor X").
3. Pulsa **Guardar**.

![Movimiento manual](img/stock-movement-form.png)

### Filtrar movimientos

En la parte superior puedes filtrar por:

- **Insumo**.
- **Tipo** de movimiento.
- **Rango de fechas**.

### Exportar a CSV

1. Aplica los filtros (opcional).
2. Pulsa **Exportar CSV**.
3. La app genera un archivo con todas las columnas: fecha, insumo, tipo,
    cantidad, notas.

## Pestaña Alertas

Muestra todos los insumos cuyo stock actual es **igual o inferior** al stock
mínimo.

![Alertas de stock](img/inventory-alerts.png)

Cada alerta muestra:

- Nombre del insumo.
- Stock actual vs mínimo.
- Unidad.

!!! tip "Consejo"
    Revisa las alertas al inicio del turno para hacer pedidos a proveedores con
    tiempo.

## Cómo se descuenta el stock automáticamente

El sistema descuenta stock al **completar una transacción SALE** (cobro
exitoso). Para cada producto vendido:

1. El sistema busca la receta (ver [Recetas de inventario](recetas-inventario.md)).
2. Multiplica la cantidad vendida por las cantidades de la receta.
3. Descuenta del stock actual.
4. Registra un movimiento tipo `SALE` por cada insumo.

Si una receta falta o un insumo no existe, el sistema:

- Registra una **advertencia** (visible en los logs del servidor).
- **No bloquea** la venta.
- El stock no se descuenta.

## Unidades del sistema

Todas las cantidades se manejan internamente en su **unidad base**:

- `KG`, `G` (peso): la conversión interna es 1 KG = 1000 G.
- `L`, `ML` (volumen): 1 L = 1000 ML.
- `UNIT`, `CAJA`, `DOCENA` son unidades discretas.

Al registrar movimientos, respeta la unidad del insumo.