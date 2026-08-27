# Sincronización en tiempo real

Restic mantiene sincronizadas las pantallas de **Pedidos**, **Comandas** y
**Caja** entre todos los dispositivos conectados a la misma sucursal.

**Rol requerido:** Todos los usuarios.

## ¿Qué se sincroniza?

| Evento | Dispositivos notificados |
|---|---|
| Se **crea** un pedido | Todos (los meseros ven el pedido aparecer; cocina lo ve en comandas; caja lo ve en pendientes). |
| Se **modifica el estado** de un pedido o un ítem | Todos (los chips de estado cambian en vivo). |
| Se **agregan productos** a un pedido existente | Todos (especialmente relevante para cocina, que ve solo los items nuevos). |
| Se **cambia el estado de un detalle** (comanda) | Meseros y cajeros (para saber qué está listo). |
| Se **cobra** un pedido (transacción SALE) | Todos (el pedido desaparece de pendientes y aparece en historial). |

## ¿Cómo funciona?

La app mantiene una conexión WebSocket con el servidor. Cuando ocurre un evento
relevante, el servidor publica un mensaje en un **tópico** de la sucursal y
todos los dispositivos suscritos lo reciben.

### Tópicos principales

- `orders/created` — pedidos nuevos.
- `orders/open` — lista completa de pedidos abiertos del día.
- `orders/status` — cambios de estado de un pedido.

### Suscripción

La app se suscribe automáticamente al iniciar sesión. Solo se conecta a los
tópicos de la **sucursal activa**.

!!! tip "Una sola sucursal activa"
    La app solo sincroniza la sucursal con la que iniciaste sesión. Si tienes
    varias sucursales, debes cerrar sesión y volver a iniciar en la otra para
    ver sus eventos.

## ¿Qué ve el usuario?

No necesitas hacer nada: las actualizaciones se reflejan automáticamente en
las listas. Por ejemplo:

- Creas un pedido desde el celular del salón → aparece instantáneamente en la
    pantalla de Comandas de la cocina y en la pantalla de Caja.
- Cocina marca un ítem como "Preparado" → el mesero ve el cambio en su pantalla
    de Pedidos.
- Cajero cobra un pedido → el pedido desaparece de Pendientes y aparece en
    Historial sin necesidad de refrescar.

## Reconexión automática

Si la conexión WebSocket se cae (por ejemplo, por pérdida de Wi-Fi temporal):

1. La app intenta reconectar automáticamente con **backoff exponencial** (1s,
    2s, 5s, 10s, 30s).
2. Si tras 5 intentos no logra reconectar, muestra un indicador de "sin
    conexión".
3. Al recuperar la conexión, la app **sincroniza el estado completo** pidiendo
    la lista actual de pedidos al servidor.

!!! note "Sin tiempo real = operación normal"
    Si la conexión no se restablece, la app sigue funcionando: puedes seguir
    tomando pedidos, cobrándolos, etc. Lo único que pierdes es la actualización
    automática; verás datos del último momento en que hubo conexión.
    Los demás dispositivos, al recuperar la conexión, también sincronizarán.

## Compatibilidad entre web y móvil

La misma sincronización aplica entre la app móvil y la app web (si la usas).
Ambas consumen los mismos tópicos del servidor.

## Limitaciones

- La sincronización es **por sucursal**. No se sincronizan pedidos entre
    sucursales distintas.
- La reconexión puede tardar unos segundos. Si necesitas datos en tiempo real
    críticos (por ejemplo, en cocina), ten paciencia o usa el botón de
    **refrescar manualmente** (pull-to-refresh).
- Si estás en **modo avión** o sin red, la app no se conecta. Al recuperar la
    red, intenta la conexión automáticamente.