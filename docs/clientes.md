# Clientes

El módulo **Clientes** gestiona la base de datos de clientes del local,
fundamental para pedidos de **Domicilio** y **Para llevar**.

**Rol requerido:** Mesero, Cajero, Administrador (lectura y edición).
Solo `ADMINISTRADOR` puede **eliminar**.

## Pantalla principal

Menú lateral → **Clientes**.

![Pantalla Clientes](img/customers.png)

- Lista todos los clientes de la sucursal.
- Buscador por nombre, apellido, teléfono o documento.
- Botón flotante **+** para crear un cliente.

## Crear un cliente

1. Pulsa el botón **+**.
2. Completa el formulario:
    - **Nombre** (obligatorio).
    - **Apellido** (opcional pero recomendado).
    - **Documento** (cédula, NIT, etc.; único por sucursal).
    - **Teléfono** (obligatorio; único por sucursal).
    - **Email** (opcional; único por sucursal).
    - **Dirección** (opcional, útil para domicilios).
    - **Notas** (opcional; por ejemplo, "Cliente VIP", "Alérgico a los
        frutos secos").
3. Pulsa **Guardar**.

![Formulario de cliente](img/customer-form.png)

!!! warning "Importante"
    - Los campos **documento**, **teléfono** y **email** son únicos por
        sucursal.
    - El sistema valida formato de email y teléfono.

## Editar un cliente

1. Toca el cliente en la lista.
2. Modifica los campos.
3. Pulsa **Guardar**.

## Eliminar un cliente

1. Toca el cliente → **Eliminar** (icono papelera).
2. Confirma.

!!! warning "Restricción"
    - Solo `SUPER` y `ADMINISTRADOR` pueden eliminar.
    - Si el cliente tiene **pedidos abiertos**, no se puede eliminar. Primero
        cierra o anula esos pedidos.
    - Si tiene pedidos históricos, el sistema **desvincula** al cliente (no
        borra los pedidos).

## Cliente predeterminado

Si atiendes a un mismo cliente con mucha frecuencia (por ejemplo, el dueño de
una empresa que pide almuerzos a diario), puedes marcarlo como **predeterminado**.

1. En la lista de clientes, toca el ícono de **estrella** junto al cliente.
2. La estrella se llena y queda seleccionado como predeterminado.
3. Al tomar un pedido de tipo **Para llevar** o **Domicilio**, la app
    autoselecciona este cliente.

![Cliente predeterminado](img/default-customer.png)

!!! tip "Cambiar el predeterminado"
    Solo puede haber **un cliente predeterminado** a la vez. Si marcas otro,
    el anterior deja de serlo automáticamente.

## Búsqueda rápida al tomar pedidos

Al tomar un pedido, la pantalla de selección de cliente muestra un buscador
que:

- Filtra por nombre, apellido o teléfono.
- Es **case-insensitive** (no distingue mayúsculas).
- Muestra resultados al escribir (sin necesidad de pulsar Enter).

## Buenas prácticas

- Captura el **teléfono** siempre; es el dato más usado para contactar al
    cliente.
- Usa el campo **Notas** para alergias, preferencias o datos importantes
    (ej. "Pide todo sin picante").
- Para clientes corporativos, registra el **NIT** para emitir factura
    electrónica.