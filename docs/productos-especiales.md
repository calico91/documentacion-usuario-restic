# Productos especiales

Restic admite cuatro tipos de producto. Aquí se explica cómo elegirlos y
configurarlos al tomar un pedido.

**Rol requerido:** Mesero, Administrador (al tomar pedidos).

## Resumen de tipos

| Tipo | Cómo se comporta al pedirlo |
|---|---|
| **SIMPLE** | Un solo precio; se agrega directamente. |
| **VARIABLE** | Varios precios por tamaño; la app pide elegir el tamaño. |
| **COMBO** | Tiene grupos con opciones (mínimo y máximo); se abre un diálogo para armar el combo. |
| **COMBINADO** | Producto 2x1; se cobra el más caro y el acompañante es gratis. |

## Producto SIMPLE

Es el más común: un nombre, una descripción y un precio.

1. Toca el botón **+** del producto.
2. Aparece en el carrito con cantidad 1.
3. Si quieres, toca el ícono de **lápiz/editar** para añadir un comentario
    (por ejemplo, "término medio").

![Producto simple](img/product-simple.png)

## Producto VARIABLE (por tamaño)

Tiene varios precios con etiquetas como "12 oz", "16 oz", "Grande".

1. Toca el botón **+** del producto.
2. La app abre un diálogo con las tallas disponibles.
3. Elige la talla y la cantidad.
4. Pulsa **Agregar**.

![Selector de tamaño](img/product-variable.png)

!!! note "Cambio de precio"
    Si el producto cambió de precio, la app usa siempre el precio **vigente** al
    momento del pedido.

## Producto COMBO

Está compuesto por **grupos**, cada uno con opciones. Por ejemplo: "Combo
almuerzo" con grupo "Proteína" (mínimo 1, máximo 1) y grupo "Acompañamiento"
(mínimo 1, máximo 2).

1. Toca el botón **+** del producto.
2. La app abre el diálogo **Armar combo** con todos los grupos.
3. Para cada grupo, selecciona las opciones requeridas.
    - Si el grupo tiene mínimo/máximo, la app valida antes de permitirte agregar.
    - Si una opción tiene precio adicional, se suma al total del combo.
4. Puedes armar **varias unidades del mismo combo** con el selector en la parte
    superior.
5. Añade un **comentario por unidad** si lo necesitas.
6. Pulsa **Agregar al pedido**.

![Armar combo](img/product-combo.png)

!!! warning "Importante"
    - Los grupos **requeridos** (mínimo > 0) deben tener al menos esa cantidad
        de opciones elegidas.
    - Si excedes el **máximo**, la app marca los chips en rojo y bloquea el botón
        **Agregar**.

!!! tip "Comentario por unidad"
    Si pides 3 combos iguales pero cada uno con notas distintas (por ejemplo,
    uno sin picante), usa el campo de comentario por unidad.

## Producto COMBINADO (2x1)

Es un producto que viene con un acompañante. La app cobra **solo el más caro** de
los dos.

1. Toca el botón **+** del producto.
2. La app muestra los productos **hermanos** (otros `COMBINADO` configurados
    como acompañantes).
3. Elige el acompañante con el selector.
4. Define la cantidad.
5. Pulsa **Agregar**.

![Combinado 2x1](img/product-combinado.png)

!!! note "Cobro"
    El precio aplicado es el **mayor** entre el producto principal y el
    acompañante elegido. Esto se refleja en el resumen del pedido con el badge
    **"🔗 COMBINADO 2×1"**.

!!! tip "Útil para"
    Promociones tipo "paga uno y llévate otro", combos de helado con topping,
    menú + bebida, etc.

## Productos "Opción de combo"

Algunos productos solo existen como **opciones dentro de combos** (por ejemplo,
"Porción extra de papas"). Esos productos:

- **No aparecen** en el catálogo principal al tomar pedidos.
- Muestran el badge **"Opción"** en el módulo **Menú**.
- Solo se pueden elegir al armar un combo.

![Producto opción de combo](img/product-option-only.png)