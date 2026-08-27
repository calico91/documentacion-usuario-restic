# Solución de problemas

Esta sección agrupa los problemas más frecuentes y cómo resolverlos.

## Inicio de sesión

### "El servidor no responde"

- **Causa**: la URL del servidor está mal configurada, o el dispositivo no tiene
    acceso a la red local.
- **Solución**:
    1. Pulsa **"Configurar conexión"** en la pantalla de login.
    2. Verifica la URL (incluye `http://` y el puerto, usualmente `8093`).
    3. Confirma que el dispositivo esté en la misma Wi-Fi que el servidor.
    4. Prueba abrir la URL en el navegador del celular para confirmar.

### "Credenciales inválidas"

- **Causa**: usuario o contraseña incorrectos.
- **Solución**:
    1. Verifica mayúsculas/minúsculas.
    2. Si la contraseña es temporal y ya la usaste, no funcionará; pide al
        admin que la restablezca.
    3. Si no recuerdas tu contraseña, pide al administrador un reset.

### "Demasiados intentos, intenta más tarde"

- **Causa**: más de 10 intentos de login en menos de un minuto.
- **Solución**: espera un minuto y reintenta.

### "Su sesión ha expirado"

- **Causa**: el token de sesión expiró (tras inactividad) o se inició sesión en
    otro dispositivo.
- **Solución**: vuelve a iniciar sesión.

### La app me devuelve al login sin razón aparente

- **Causa**: se inició sesión en otro dispositivo con el mismo usuario. Restic
    solo permite **una sesión activa por usuario**.
- **Solución**: cierra sesión en el otro dispositivo, o usa solo uno a la vez.

## Pedidos

### "No se puede crear el pedido: mesa no disponible"

- **Causa**: otro pedido activo usa la misma mesa.
- **Solución**: elige otra mesa, o espera a que se cierre/cobre el pedido
    activo.

### "Selecciona al menos un producto"

- **Causa**: estás intentando confirmar un pedido con el carrito vacío.
- **Solución**: agrega al menos un producto antes de confirmar.

### "Producto no disponible"

- **Causa**: el producto fue desactivado o eliminado desde el módulo Menú.
- **Solución**: pide al administrador que reactive el producto, o elige otro.

## Impresora

### La impresora no aparece en la lista Bluetooth

- **Causa**: la impresora está apagada o no está en modo emparejamiento.
- **Solución**:
    1. Enciende la impresora.
    2. Ponla en modo emparejamiento (revisa el manual; normalmente con un
        botón).
    3. Pulsa **Escanear dispositivos** en la app.

### La conexión Bluetooth se pierde frecuentemente

- **Causa**: dispositivo móvil lejos de la impresora, o interferencias.
- **Solución**:
    1. Acércate a la impresora.
    2. Evita obstáculos (paredes gruesas, microondas).
    3. Reinicia Bluetooth del dispositivo.

### La impresora de red no responde

- **Causa**: IP incorrecta, puerto bloqueado, o impresora apagada.
- **Solución**:
    1. Verifica la IP en la configuración de la impresora.
    2. Comprueba que el dispositivo y la impresora estén en la misma red.
    3. Prueba con `ping {IP}` desde otro dispositivo de la red.
    4. Si usas un firewall, confirma que el puerto `9100` esté abierto.

### El ticket se imprime con caracteres raros

- **Causa**: tamaño de papel mal configurado (la app envía bytes para 58 mm o
    80 mm).
- **Solución**: ajusta el tamaño de papel en la configuración de la impresora.

## Caja

### "No hay caja abierta"

- **Causa**: no iniciaste un turno de caja.
- **Solución**: ve a **Opciones de caja → Apertura** y abre el turno.

### "Terminal ya tiene una caja abierta"

- **Causa**: otro cajero abrió un turno en ese terminal.
- **Solución**: pídele al otro cajero que cierre su turno, o elige otro
    terminal.

### Diferencia alta al cerrar caja

- **Causa**: faltante o sobrante significativo de efectivo.
- **Solución**:
    1. Verifica que hayas registrado todos los egresos del turno.
    2. Confirma el efectivo físico (cuenta varias veces).
    3. Anota una observación clara en el formulario de cierre.
    4. Si el faltante es grande, repórtalo al administrador antes de cerrar.

## Facturación

### La factura no se envía por email

- **Causa**: error temporal del servidor de email, o email del cliente
    incorrecto.
- **Solución**:
    1. Verifica que la factura tenga un email registrado.
    2. El sistema reintenta automáticamente hasta 3 veces.
    3. Un administrador puede forzar un reintento desde la pantalla de
        facturas.

### "No se puede cambiar el método de pago"

- **Causa**: solo `SUPER` y `ADMINISTRADOR` pueden cambiar el método de pago
    post-cobro.
- **Solución**: pide a un administrador que haga el cambio.

## Actualización de la app

### "Debes actualizar la app"

- **Causa**: la versión instalada es anterior a la mínima requerida.
- **Solución**:
    1. Pulsa **Abrir tienda** en la pantalla de actualización.
    2. Descarga e instala la nueva versión.
    3. Vuelve a abrir la app y pulsa **Reintentar** si la pantalla persiste.

## Contactar a soporte

Si después de intentar las soluciones anteriores el problema persiste:

1. Anota el **mensaje de error exacto**.
2. Toma una **captura de pantalla** si es posible.
3. Indica la **versión de la app** (visible en la pantalla de login).
4. Indica el **módulo/función** donde ocurre.
5. Contacta al administrador del sistema o al equipo de soporte con esa
    información.