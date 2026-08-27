# Mesas

El módulo **Mesas** gestiona las mesas del local: alta, edición, eliminación,
reserva y liberación.

**Rol requerido:** Administrador (CRUD), Mesero (reservar / liberar).

## Pantalla principal

Menú lateral → **Mesas**.

![Pantalla Mesas](img/tables.png)

- Las mesas se muestran en una **grilla de 2 columnas** con un chip de estado:
    - 🟢 **Disponible** (verde).
    - 🟠 **Ocupada** (naranja).
    - 🔵 **Reservada** (azul).
- Cada tarjeta muestra: nombre, número, ubicación y estado.

## Crear una mesa

1. Pulsa el botón **Nueva mesa**.
2. Completa el formulario:
    - **Nombre** (ej. "Mesa 1", "Barra 3").
    - **Número** — identificador numérico (si lo dejas vacío, se asigna el
        siguiente automáticamente).
    - **Ubicación** (ej. "Salón principal", "Patio", "Barra").
    - **Estado** inicial (normalmente "Disponible").
3. Pulsa **Guardar**.

![Formulario de mesa](img/table-form.png)

## Editar o eliminar una mesa

1. Toca la mesa en la grilla.
2. Pulsa el ícono de **lápiz** para editar o **papelera** para eliminar.
3. Confirma.

!!! warning "Importante"
    - Eliminar una mesa con pedidos activos **no se permite**. Primero cierra o
        anula esos pedidos.
    - Eliminar una mesa **no** afecta pedidos históricos; solo deja de estar
        disponible para nuevos pedidos.

## Reservar mesas

Útil para apartar mesas antes de que lleguen los clientes (cumpleaños,
reservaciones).

1. Mantén pulsada una mesa disponible (o selecciónala si ya hay otras
    seleccionadas).
2. Selecciona todas las mesas que quieras reservar (multi-selección).
3. Pulsa **Reservar** en el FAB.
4. Confirma.

!!! note "Reserva atómica"
    Si alguna mesa de la selección **no se puede reservar** (por ejemplo, ya
    está ocupada), **ninguna** se reserva. La operación es atómica.

![Reservar mesas](img/reserve-tables.png)

## Liberar mesas

Cuando los clientes con reserva confirmada llegan y se instalan, o cuando
cancela la reserva:

1. Selecciona las mesas reservadas.
2. Pulsa **Liberar**.
3. Confirma.

!!! tip "Estados y transiciones"
    ```
    Disponible → (Crear pedido SALON) → Ocupada
    Disponible → (Reservar) → Reservada → (Liberar) → Disponible
    Ocupada → (Cobrar transacción SALE) → Disponible
    ```

## Cambio automático de estado

El sistema actualiza el estado de las mesas automáticamente:

- Cuando se **crea un pedido de tipo SALÓN**, las mesas asociadas pasan a
    **Ocupada**.
- Cuando se **cobra un pedido** (transacción SALE completada), las mesas
    vuelven a **Disponible**.
- Al **anular un pedido**, las mesas asociadas vuelven a **Disponible**.

## Buenas prácticas

- Mantén la **numeración** consistente para evitar confusión con los clientes.
- Usa **ubicaciones** claras para que los meseros ubiquen rápido las mesas.
- Si tu local tiene **mesas móviles** (que se unen o separan), documenta la
    convención interna y usa nombres claros.