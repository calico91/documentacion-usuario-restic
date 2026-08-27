# Zonas de impresión

Las **zonas de impresión** representan las impresoras térmicas físicas
conectadas a tu red local. Puedes asignar cada categoría de menú a una zona
para que sus comandas se impriman en una impresora específica.

**Rol requerido:** Administrador, Cajero.

## ¿Por qué zonas?

En un restaurante es común tener impresoras en distintos lugares:

- Cocina caliente.
- Cocina fría (ensaladas).
- Barra (tragos).
- Caja (facturas).
- Repostería.

Las zonas permiten enrutar las comandas a la impresora correcta sin imprimir
todo en un solo lugar.

## Pantalla de zonas

**Configuración de impresora → Zonas de impresión**.

![Zonas de impresión](img/printer-zones.png)

- Lista todas las zonas configuradas.
- Cada zona muestra: nombre, IP, puerto, número de categorías asignadas.

## Crear una zona

1. Pulsa el botón **+**.
2. Completa:
    - **Nombre** (ej. "Cocina", "Barra", "Caja").
    - **IP** — la dirección IP local de la impresora (ej. `192.168.1.50`).
    - **Puerto** — normalmente `9100` (estándar para impresoras de red).
3. Pulsa **Guardar**.

![Crear zona](img/printer-zone-form.png)

!!! tip "Encontrar la IP de la impresora"
    - Revisa el manual de la impresora.
    - Imprime una página de autotest (normalmente con el botón FEED).
    - En la configuración de tu router, busca dispositivos conectados.

!!! warning "Importante"
    La IP debe ser **alcanzable** desde el dispositivo móvil. Verifica que el
    celular y la impresora estén en la misma red local (misma Wi-Fi / VLAN).

## Editar o eliminar una zona

1. Toca la zona en la lista.
2. Modifica los campos o pulsa **Eliminar**.
3. Confirma.

## Asignar categorías a zonas

1. Ve a **Configuración de impresora → Zonas de impresión** → **Asignar
    categorías**.
2. Verás una lista de categorías de menú.
3. Para cada categoría, selecciona la zona (impresora) a la que se enviarán
    sus comandas.

![Asignar zonas](img/zone-assign.png)

!!! tip "Asignación masiva"
    Usa el botón **"Asignar todas las no asignadas"** para asignar en bloque
    todas las categorías que aún no tengan zona.

## Asignación por defecto

- Si una categoría **no tiene zona asignada**, sus comandas se imprimen en la
    **impresora por defecto** (la primera de la lista o la que esté marcada
    como predeterminada).
- Si no hay ninguna zona configurada, las comandas **no se imprimen** (la
    venta se completa, pero no se genera ticket físico).

## Resolución de conflictos

Si dos categorías tienen la misma zona pero el dispositivo no llega a esa
impresora, las comandas fallarán. La app muestra un error y no bloquea la
venta, pero los tickets no se imprimirán. Verifica la conectividad.

## Buenas prácticas

- Usa **nombres claros** que identifiquen la ubicación física (ej.
    "Cocina-Caliente" en vez de solo "Cocina").
- Documenta la **IP** de cada impresora en un lugar accesible para cuando
    falle la conexión.
- Configura la **asignación de zonas** antes de empezar a operar; cambiar
    zonas con la tienda abierta puede causar reimpresiones inesperadas.