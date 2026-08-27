# Requisitos

Antes de empezar, asegúrate de que tu dispositivo y tu local están listos para
usar Restic.

## Requisitos del dispositivo

- **Sistema operativo:** Android 8.0 (Oreo) o superior.
- **RAM mínima:** 2 GB recomendados.
- **Almacenamiento:** 100 MB libres.
- **Conectividad:** Wi-Fi o datos móviles con acceso a la red local donde está
  instalado el servidor de Restic.
- **Bluetooth:** requerido solo si vas a usar una impresora térmica Bluetooth.

## Requisitos del local

- **Servidor Restic** instalado y encendido, accesible desde la red local. Tu
  administrador te indicará la dirección (por ejemplo, `http://192.168.1.10:8093`).
- **Sucursal registrada** en el sistema con un usuario asignado a tu nombre y rol.
- Si vas a imprimir tickets: **impresora térmica** compatible (Bluetooth o red,
  58 mm o 80 mm), emparejada o conectada a la misma red.

!!! tip "Consejo"
    Antes del primer turno, prueba la conexión desde el celular abriendo la
    dirección del servidor en el navegador. Si carga, la app también podrá.

## Requisitos de la cuenta

- **Usuario y contraseña** entregados por tu administrador.
- Si es la primera vez, tu contraseña puede ser temporal; la app te pedirá
    cambiarla al iniciar sesión.

## Permisos de la app

La app puede solicitar los siguientes permisos en el dispositivo:

| Permiso | Cuándo se pide | Para qué |
|---|---|---|
| Internet | Al instalar | Conectar con el servidor Restic |
| Bluetooth (conectar + escanear) | Al configurar impresora Bluetooth | Buscar y emparejar impresoras |
| Almacenamiento | Al exportar archivos CSV o tickets | Guardar el archivo temporalmente para compartirlo |

No requiere permisos de cámara, ubicación ni contactos.