# Iniciar sesión

Una vez configurada la URL del servidor, puedes iniciar sesión con tu usuario y
contraseña.

## Procedimiento

1. Abre la app Restic.
2. En la pantalla de inicio de sesión, escribe tu **usuario** (en minúsculas, sin
    espacios) y tu **contraseña**.
3. Toca el ícono del **ojo** si quieres mostrar/ocultar la contraseña.
4. Pulsa **Ingresar**.

![Pantalla de inicio de sesión](img/login.png)

## Selección de sucursal

Si tu usuario está asignado a **varias sucursales**, después de iniciar sesión la
app mostrará un selector de sucursal:

![Selector de sucursal](img/branch-selection.png)

1. Toca la sucursal en la que vas a trabajar.
2. Pulsa **Confirmar** (o simplemente selecciónala; la app avanza al inicio).

Si solo tienes una sucursal asignada, la app entra directamente al inicio sin
pedir selección.

## Cambio de contraseña obligatorio

Si tu contraseña es temporal (por ejemplo, recién creado por el administrador),
la app te llevará primero a la pantalla **Cambiar contraseña**. Tras cambiarla,
volverás al inicio y podrás operar normalmente.

!!! warning "Importante"
    No puedes saltarte el cambio de contraseña si el sistema lo solicita.

## Inicio (Home)

Una vez dentro, verás la pantalla principal con:

- Una **barra inferior** con tres pestañas principales: **Pedidos**, **Comandas**
    y **Caja** (según los módulos habilitados en tu rol).
- Un **menú lateral** (botón hamburguesa o arrastre desde la izquierda) con el
    resto de secciones: usuarios, menú, mesas, configuración, etc.

![Pantalla principal (Home)](img/home.png)

## Errores frecuentes

| Mensaje | Causa probable | Solución |
|---|---|---|
| "El servidor no responde" | URL mal configurada o sin red | Verifica [Configurar conexión](configurar-conexion.md). |
| "Credenciales inválidas" | Usuario o contraseña incorrectos | Confirma con tu administrador; respeta mayúsculas. |
| "Demasiados intentos, intenta más tarde" | Más de 10 intentos de login en 1 minuto | Espera un minuto antes de reintentar. |
| "Su sesión ha expirado" | El token expiró o se cerró en otro dispositivo | Vuelve a iniciar sesión. |

!!! tip "Consejo"
    Si la app se cierra sola y te devuelve al login, el sistema detectó que otra
    pestaña o dispositivo inició sesión con el mismo usuario. Restic solo permite
    **una sesión activa por usuario** a la vez.