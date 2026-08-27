# Comandas (vista de cocina)

La pestaña **Comandas** es la pantalla principal del cocinero: muestra todos los
pedidos abiertos con sus productos pendientes de preparar.

**Rol requerido:** Cocinero, Administrador.

## Pantalla principal

1. En la barra inferior, toca **Comandas**.
2. Verás dos pestañas:
    - **Pendientes** — pedidos en estado **Abierto**.
    - **Historial** — pedidos finalizados (solo consulta).

![Comandas pendientes](img/commands-pending.png)

### Por cada pedido verás

- Número de pedido.
- Tipo: **Salón**, **Para llevar**, **Domicilio**.
- Si es salón: número de mesa.
- Si es take-away o domicilio: nombre del cliente.
- Fecha y hora.
- Lista de ítems con su **estado de cocina**:
    - 🕐 **Pendiente** — aún no se empezó.
    - 🍳 **En preparación** — se está cocinando.
    - ✅ **Preparado** — listo para entregar.
    - ❌ **Anulado** — no se prepara.
- Observaciones generales y notas por ítem.

!!! tip "Actualización en vivo"
    Las comandas se actualizan en tiempo real cuando:
    - Llega un pedido nuevo.
    - Otro cocinero avanza el estado de un ítem.
    - Se anula un ítem desde el módulo Pedidos o Caja.
    No necesitas refrescar manualmente.

## Avanzar el estado de los ítems

1. Toca un pedido para abrir el detalle de cocina.
2. Selecciona los ítems que vas a marcar (checkboxes).
3. Elige el nuevo estado:
    - **En preparación** — empieza a cocinar.
    - **Preparado** — listo para entregar al mesero o mostrador.
4. Pulsa **Confirmar**.

![Marcar como preparado](img/commands-advance.png)

### Flujo recomendado

```
Pendiente → En preparación → Preparado → (Servido, lo marca el mesero)
```

- **Servido** lo marca el **mesero** desde la pantalla de Pedidos cuando entrega
    el producto al cliente.
- Si anulas un ítem, el estado se propaga al pedido y se descuenta del total.

!!! warning "Importante"
    - La anulación de un ítem descuenta inventario (si tiene receta asociada).
    - Si anulas todos los ítems de un pedido, este pasa automáticamente a
        **Finalizado**.

## Filtrado por fecha

- La barra superior tiene un selector de fecha ◀ ▶.
- Permite revisar comandas de días anteriores.
- Por defecto muestra el día actual.

## Imprimir comandas adicionales

Si necesitas reimprimir la comanda de un pedido (por ejemplo, se perdió el
ticket):

1. Toca el pedido.
2. Pulsa el ícono de **impresora** en el detalle.
3. La comanda se envía a las impresoras configuradas para cada categoría/zona.

## Solución de problemas

| Problema | Causa probable | Solución |
|---|---|---|
| No aparecen pedidos | Las comandas están en otra fecha | Cambia la fecha en el selector. |
| El estado no se actualiza | Problema temporal de conexión | Espera unos segundos; la app sincroniza automáticamente. |
| Ítems en gris/tachado | Anulados desde Pedidos o Caja | No se pueden revertir aquí; debes gestionar desde Pedidos. |