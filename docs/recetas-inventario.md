# Recetas de inventario

Las recetas vinculan un **producto** con uno o varios **insumos** del inventario.
Cuando se vende el producto, los insumos se descuentan automáticamente del
stock.

**Rol requerido:** Administrador.

## ¿Cuándo usar recetas?

- Productos que consumen ingredientes físicos (hamburguesas, pizzas, cafés con
    leche, etc.).
- Productos **COMBO** y **COMBINADO** también pueden tener recetas.
- Si tienes activado el switch **"Requiere receta de inventario"** en un
    producto, debes configurarla antes de poder venderlo (o se mostrará una
    advertencia al cobrar).

## ¿Dónde se configura?

1. Menú lateral → **Menú**.
2. Selecciona la categoría y subcategoría del producto.
3. Toca el producto.
4. En el menú emergente, pulsa **Configurar receta**.

![Configurar receta](img/recipe-menu.png)

## Pantalla de recetas

![Formulario de receta](img/recipe-form.png)

- Lista los **insumos** vinculados y la cantidad que consume cada unidad
    vendida del producto.
- Si el producto es **VARIABLE**, puedes definir una receta diferente por cada
    tamaño (precio variante).
- Botones:
    - **Agregar insumo**.
    - **Editar línea** (cantidad).
    - **Eliminar línea**.
    - **Guardar todo**.
    - **Eliminar receta completa**.

## Agregar un insumo a la receta

1. Pulsa **Agregar insumo**.
2. Busca el insumo por nombre.
3. Escribe la **cantidad** (en la unidad del insumo: kg, g, l, ml, unidades,
    cajas, docenas).
4. Pulsa **Guardar**.

!!! example "Ejemplo"
    Producto: **Hamburguesa clásica**
    Receta:
    - Pan: 1 unidad
    - Carne 120g: 0.12 kg
    - Queso: 0.03 kg
    - Lechuga: 0.02 kg
    - Tomate: 0.03 kg

## Receta por variante (productos VARIABLE)

Si tu producto tiene varios precios (por ejemplo, "Café 12oz" y "Café 16oz"):

1. En el selector de variante, elige el tamaño.
2. Configura los insumos y cantidades específicos para esa variante.
3. Repite para cada variante.

Si no defines una variante específica, el sistema usará la receta del producto
base (si existe).

!!! warning "Importante"
    - Para productos **VARIABLE**, es **obligatorio** definir una receta por
        cada variante. El sistema valida al guardar.
    - Para productos **no VARIABLE**, la receta es única (sin variante).

## Descontar stock al vender

Cuando se cobra un pedido, el sistema:

1. Identifica los productos vendidos.
2. Para cada producto, busca su receta.
3. Multiplica la cantidad vendida por las cantidades de la receta.
4. Descuenta del stock actual del insumo.

Si una receta falta o está incompleta:

- El sistema registra una **advertencia** (WARN).
- El cobro **no se bloquea**: la venta se completa igualmente.
- Pero el stock no se descuenta, lo que puede causar inconsistencias.

!!! tip "Monitorea el inventario"
    Revisa regularmente el módulo **Inventario → Alertas** para detectar
    productos con stock bajo antes de que se agoten.

## Eliminar una receta

1. Abre el producto → **Configurar receta**.
2. Pulsa **Eliminar receta completa**.
3. Confirma.

!!! warning "Importante"
    Eliminar una receta no afecta los pedidos ya cobrados. Pero a partir de ese
    momento, las nuevas ventas **no descontarán stock** hasta que vuelvas a
    configurar la receta.

## Buenas prácticas

- Define recetas para **todos** los productos que consumen insumos, aunque sean
    pocos (vasos, servilletas, etc.).
- Si modificas una receta, recuerda que solo aplica a **futuras ventas**. Las
    ventas ya cobradas no recalculan su descuento de stock.
- Coordina con el equipo de cocina para mantener las cantidades actualizadas
    (por ejemplo, si el pan cambia de gramaje).