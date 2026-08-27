# Configurar la conexión al servidor

Antes del primer inicio de sesión, debes indicarle a la app la dirección del
servidor Restic. Este paso solo es necesario la primera vez, o si cambia la
dirección del servidor.

## ¿Cuándo configurar la conexión?

- **Primera instalación**: la app viene sin servidor configurado.
- **Cambio de servidor** (por mudanza o nuevo部署): necesitas actualizar la URL.
- **Cambio de red**: si el servidor cambió de IP local.

## Procedimiento

1. Abre la app. Verás la pantalla de inicio de sesión.
2. Pulsa el enlace **"Configurar conexión"** (icono de engranaje) en la parte
    inferior.

![Login con enlace Configurar conexión](img/login-configurar.png)

3. Se abrirá un cuadro de diálogo con el campo **URL del servidor**.

    ![Modal de configuración](img/configurar-conexion-modal.png)

4. Escribe la dirección completa, por ejemplo:
    - `http://192.168.1.10:8093`
    - `http://10.0.0.5:8093`
    - `https://restic.miempresa.com`
5. Pulsa **Guardar**.

!!! warning "Importante"
    - Incluye `http://` o `https://` al inicio.
    - No incluyas la barra final ni rutas adicionales (como `/api`).
    - El puerto suele ser `8093`, pero tu administrador puede indicarte otro.

## ¿Y si me equivoco?

- Vuelve a pulsar **"Configurar conexión"** y corrige la URL.
- O pulsa **Restablecer** en el mismo modal para volver a la URL por defecto.

## Resultado esperado

Al volver a la pantalla de inicio de sesión, ya puedes escribir tu usuario y
contraseña. La app recordará la URL hasta que la cambies nuevamente.

!!! tip "Consejo"
    Si la app no responde al pulsar **Ingresar** y muestra "El servidor no
    responde", revisa la URL. El dispositivo debe estar en la misma red local que
    el servidor (misma Wi-Fi o VLAN).