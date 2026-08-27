# Tomar un pedido

Esta es la pantalla principal del mesero: permite crear un pedido nuevo eligiendo
el tipo, las mesas, el cliente y los productos.

**Rol requerido:** Mesero, Administrador.

## Antes de empezar

Asegúrate de tener:

- Sesión iniciada y sucursal seleccionada.
- Módulo **TOMAR_PEDIDO** habilitado en tu rol.
- El menú ya tiene categorías y productos cargados (visible en la pestaña
    **Pedidos**; si está vacío, avisa al administrador).

## Procedimiento

### 1. Abrir "Tomar pedido"

1. En la pestaña **Pedidos** pulsa el botón **+ Crear pedido**.

![Botón Crear pedido](img/orders-create-button.png)

También puedes acceder desde el menú lateral → **Pedidos** → **Crear**.

### 2. Elegir el tipo de pedido

Selecciona una de las tres opciones:

- **Salón** — el pedido se atenderá en una o varias mesas del local.
- **Para llevar** — el cliente retira en mostrador.
- **Domicilio** — el pedido se entrega a la dirección del cliente.

![Selector de tipo](img/take-order-origin.png)

!!! note "Notas"
    - **Salón** requiere seleccionar al menos una mesa.
    - **Para llevar** y **Domicilio** requieren seleccionar un cliente.

### 3. Elegir mesas (solo Salón)

1. Aparecerá la grilla de mesas disponibles.
2. Toca una o varias mesas disponibles (color verde). Las mesas ocupadas
    (naranja) o reservadas (azul) no se pueden elegir.
3. Para cambiar la selección, vuelve a tocarlas.

![Selector de mesas](img/take-order-tables.png)

### 4. Elegir cliente

1. Pulsa **Buscar cliente** o el nombre del cliente actual para abrir el buscador.
2. Escribe nombre, apellido o teléfono. La lista se filtra en vivo.
3. Toca el cliente deseado para seleccionarlo.

![Selector de cliente](img/take-order-customer.png)

!!! tip "Cliente predeterminado"
    Si siempre atiendes al mismo cliente (por ejemplo, la mayoría de pedidos a
    domicilio son para el mismo comprador), márcalo como predeterminado desde el
    módulo **Clientes**. La app lo autoseleccionará en los nuevos pedidos.

### 5. Elegir productos

1. Selecciona una **categoría** en las pestañas superiores.
2. Si la categoría tiene subcategorías, selecciona una para ver los productos.
3. Toca el botón **+** del producto para agregarlo al pedido.
4. Para añadir una **nota por producto** (por ejemplo, "sin cebolla"), toca el
    ícono de **lápiz/editar** del producto.

![Selector de productos](img/take-order-products.png)

!!! info "Tipos de producto"
    - **SIMPLE** — un solo precio.
    - **VARIABLE** — varios precios por tamaño (ej. 12 oz, 16 oz). La app te
        pedirá elegir el tamaño.
    - **COMBO** — tiene varios grupos con opciones. La app abre un diálogo para
        armar el combo.
    - **COMBINADO 2x1** — eliges un acompañante (la app cobra solo el más caro).

    Más detalles en [Productos especiales](productos-especiales.md).

### 6. Revisar el pedido y agregar cargos

1. Pulsa el botón flotante **Ver Pedido (N)** para abrir el resumen.
2. En el resumen puedes:
    - Ver el listado de productos y cantidades.
    - Cambiar cantidades con los botones **+ / −** o eliminar ítems.
    - Tocar **Agregar cargo** para sumar conceptos como domicilio o servicio.
    - Escribir **observaciones generales** del pedido (opcional).

![Resumen del pedido](img/take-order-summary.png)

### 7. Confirmar el pedido

1. Verifica el total y los productos.
2. Pulsa **Confirmar pedido**.

Al confirmar, la app:

- Crea la orden en el servidor (estado **OPEN**).
- Muestra un modal de éxito con el número de pedido.
- Ofrece **Imprimir orden** para enviar la comanda a las impresoras de cocina.
- Regresa a la pestaña **Pedidos** donde verás el pedido recién creado.

![Modal de éxito](img/take-order-success.png)

!!! tip "Cancelar a medias"
    Si sales de la pantalla con productos ya agregados, la app te preguntará si
    quieres descartar los cambios. No perderás pedidos confirmados.

## Resultado esperado

- El pedido aparece en **Pedidos** con estado **Abierto**.
- Aparece en **Comandas** para que cocina lo prepare.
- Si tiene productos configurados con zonas de impresión, se imprime la comanda
    automáticamente en las impresoras correspondientes (si están conectadas).

## Solución de problemas

| Problema | Causa | Solución |
|---|---|---|
| "Selecciona al menos una mesa" | Estás en Salón sin mesa | Toca una mesa disponible. |
| "Selecciona un cliente" | Tipo Para llevar/Domicilio sin cliente | Busca y selecciona uno. |
| "Agrega al menos un producto" | Carrito vacío | Agrega productos antes de confirmar. |
| La grilla de mesas está vacía | No hay mesas disponibles | Revisa en **Mesas** o pídele al admin que cree más. |