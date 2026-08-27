# Configurar la impresora

Restic admite impresoras térmicas conectadas por **Bluetooth** o por **red**
(Wi-Fi / Ethernet). Esta sección explica cómo configurar y probar la conexión.

**Rol requerido:** Administrador, Cajero.

## Tipos de impresora soportados

- **Bluetooth**: impresoras portátiles que se emparejan con el dispositivo.
- **Red (TCP/IP)**: impresoras conectadas a la misma red local vía Wi-Fi o
    cable Ethernet.

Ambas pueden coexistir. La app detecta automáticamente el tipo cuando se
conecta.

## Pantalla de configuración

Menú lateral → **Configuración** → **Impresora**.

![Pantalla de impresora](img/printer-settings.png)

Tiene cuatro secciones:

1. **Bluetooth** — escanear, emparejar y conectar.
2. **Red** — conectar por IP y puerto.
3. **Tamaño de papel** — 58 mm o 80 mm.
4. **Zonas de impresión** — gestión de impresoras de red por zona.

## Configurar una impresora Bluetooth

### Emparejar por primera vez

1. Enciende la impresora y ponla en modo **emparejamiento** (revisa el manual;
    normalmente manteniendo pulsado un botón).
2. En la sección **Bluetooth**, pulsa **Escanear dispositivos**.
3. La app listará los dispositivos Bluetooth cercanos.
4. Toca tu impresora en la lista.
5. Si es la primera vez, Android te pedirá confirmar el emparejamiento.
    Pulsa **Emparejar**.

### Conectar a una impresora ya emparejada

1. En la sección **Bluetooth**, la app muestra las impresoras emparejadas.
2. Toca **Conectar** sobre la impresora deseada.
3. La app indica si la conexión fue exitosa.

### Imprimir página de prueba

Una vez conectada, pulsa **Página de prueba** para enviar un ticket de prueba
a la impresora.

![Página de prueba](img/printer-test.png)

## Configurar una impresora de red

1. En la sección **Red**, escribe la **IP** de la impresora (ej.
    `192.168.1.50`).
2. Define el **puerto** (por defecto `9100`).
3. Pulsa **Conectar**.
4. Si la conexión es exitosa, la app muestra la impresora como activa.
5. Pulsa **Página de prueba** para verificar.

!!! warning "Importante"
    - El dispositivo móvil debe estar en la **misma red local** que la
        impresora.
    - Algunas impresoras requieren **configuración de red adicional** (DHCP,
        IP estática). Consulta el manual del fabricante.
    - Si la conexión falla, verifica:
        - Que la IP sea correcta (`ping` desde otro dispositivo).
        - Que el puerto sea el correcto (por defecto 9100).
        - Que el firewall de la red no bloquee el tráfico.

## Cambiar el tamaño de papel

1. En la sección **Tamaño de papel**, selecciona **58 mm** o **80 mm**.
2. La app ajusta automáticamente el layout de los tickets.

!!! tip "Diferencias"
    - **58 mm**: tickets angostos, menos información por línea, ideal para
        comandas cortas.
    - **80 mm**: tickets más anchos, más información, ideal para facturas con
        desglose.

## Indicador de conexión en la AppBar

En la barra superior de las pantallas **Pedidos** y **Caja** verás un ícono de
impresora:

- 🟢 **Verde**: al menos una impresora conectada.
- 🔴 **Rojo**: ninguna impresora conectada.
- 🟡 **Amarillo**: conectando.

## Auto-reconexión

La app intenta reconectar automáticamente a la última impresora usada:

- Al abrir la app.
- Al volver de segundo plano.
- Tras perder la conexión (por ejemplo, al alejarse del Bluetooth).

Si la reconexión falla, mostrará el ícono rojo. Puedes reconectar manualmente
desde la pantalla de configuración.

## Solución de problemas

| Problema | Causa probable | Solución |
|---|---|---|
| La impresora Bluetooth no aparece | Está apagada o no está en modo emparejamiento | Enciende y ponla en modo pairing. |
| Conexión Bluetooth exitosa pero no imprime | Cola de impresión llena o driver incompatible | Reinicia la impresora y vuelve a conectar. |
| Conexión de red falla | IP incorrecta o puerto bloqueado | Verifica con `ping` y consulta con el admin de red. |
| Imprime caracteres raros | Tamaño de papel mal configurado | Ajusta a 58 mm u 80 mm según la impresora. |
| Impresión cortada | Cabezal sucio o papel mal colocado | Limpia el cabezal y verifica la carga del papel. |