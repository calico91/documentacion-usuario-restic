# Menú y productos

El módulo **Menú** permite gestionar la estructura completa de lo que se vende:
categorías, subcategorías, productos y sus precios.

**Rol requerido:** Administrador, Cocinero (solo lectura).

## Estructura del menú

```
Categoría
├── Subcategoría
│   ├── Producto (SIMPLE / VARIABLE / COMBO / COMBINADO)
│   ├── Producto
│   └── ...
├── Producto (sin subcategoría)
└── ...
```

## Pantalla principal

Menú lateral → **Menú**.

![Pantalla Menú](img/menu.png)

- La parte superior tiene **pestañas por categoría**.
- Cada categoría lista sus **subcategorías** y, dentro, los **productos**.
- El botón flotante **+** abre el formulario de creación rápida para el nivel
    actual (categoría, subcategoría o producto según dónde estés).

## Crear una categoría

1. En la pestaña por defecto (sin categoría seleccionada), pulsa el botón **+**.
2. Completa el formulario:
    - **Nombre** (obligatorio).
    - **Descripción** (opcional).
    - **Orden** (opcional; sirve para ordenar la pestaña).
3. Pulsa **Guardar**.

## Editar o eliminar una categoría

1. Toca la pestaña de la categoría.
2. Pulsa el ícono de **lápiz** para editar, o **papelera** para eliminar.
3. Confirma.

!!! warning "Importante"
    - Eliminar una categoría **borra también** sus subcategorías y productos.
    - Si la categoría tiene productos asociados a pedidos históricos, **no se
        puede eliminar**. Primero debes migrar esos productos.

## Crear una subcategoría

1. Selecciona la categoría padre.
2. Pulsa el botón **+**.
3. Escribe el nombre y guarda.

## Crear un producto

1. Selecciona la categoría y, si aplica, la subcategoría.
2. Pulsa el botón **+**.
3. Completa el formulario:

### Campos básicos

- **Nombre** (obligatorio).
- **Descripción** (opcional, aparece al tomar el pedido).
- **Tipo** — elige entre:
    - **SIMPLE** — un solo precio.
    - **VARIABLE** — varios precios con etiquetas (ej. 12 oz, 16 oz).
    - **COMBO** — tiene grupos con opciones (ver [Combos](combos-configuracion.md)).
    - **COMBINADO** — producto 2x1 con acompañante (ver
        [Productos especiales](productos-especiales.md)).

### Switches

- **Requiere receta de inventario** — si lo activas, debes vincular el producto
    con uno o varios insumos (ver [Recetas de inventario](recetas-inventario.md)).
- **Solo opción de combo** — marca el producto como opción interna de un combo;
    no se mostrará en el catálogo principal de toma de pedidos.

### Precios

- **SIMPLE**: un único precio base.
- **VARIABLE**: una fila por cada tamaño, con su `size_label` y precio.
- **COMBO / COMBINADO**: un único precio base (puede tener adicional por opción
    de combo).

### Ejemplo: producto VARIABLE

| size_label | Precio |
|---|---|
| 12 oz | $8.000 |
| 16 oz | $10.500 |
| 20 oz | $13.000 |

## Editar un producto

1. Toca el producto en la lista.
2. Pulsa el ícono de **lápiz**.
3. Modifica los campos necesarios.
4. Pulsa **Guardar**.

## Acciones por producto

Al tocar un producto aparece un menú emergente con:

- **Editar**.
- **Configurar receta** — disponible si activaste el switch de receta.
- **Administrar combo** — disponible solo para productos tipo **COMBO**.

![Menú de producto](img/product-menu.png)

## Eliminar un producto

1. Toca el producto → **Eliminar** (icono papelera).
2. Confirma.

!!! warning "Importante"
    - Eliminar un producto **lo desactiva** si tiene pedidos históricos.
    - Un producto desactivado **no aparece** en el catálogo de toma de pedidos.

## Ordenar y filtrar

- Las categorías se ordenan por el campo **Orden** (de menor a mayor).
- Dentro de cada categoría, las subcategorías siguen el mismo orden.
- Los productos mantienen el orden en que fueron creados (puedes reordenarlos
    editándolos).