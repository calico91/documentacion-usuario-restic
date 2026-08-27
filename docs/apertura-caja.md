# Apertura de turno de caja

Antes de empezar a cobrar, debes **abrir tu turno de caja**. Esto asocia tu
usuario a un terminal y deja un registro del monto inicial en efectivo.

**Rol requerido:** Cajero, Administrador.

## ¿Cuándo abrir turno?

- Al comenzar el día o tu jornada.
- Cuando cambias de turno con otro cajero.
- Tras un cierre de caja.

## Procedimiento

1. Abre el menú lateral → **Opciones de caja** → **Apertura de caja**.

![Menú opciones de caja](img/cash-options.png)

2. Selecciona el **cajero** (si operas como supervisor a nombre de otro cajero,
    normalmente serás tú mismo).
3. Selecciona el **terminal** donde vas a operar (lista de cajas activas).
4. Escribe el **monto inicial** en efectivo con el que arrancas la caja.
5. (Opcional) Escribe **observaciones** (por ejemplo, "Efectivo de apertura
    $200.000").
6. Pulsa **Abrir caja**.

![Formulario de apertura](img/open-shift.png)

!!! warning "Importante"
    - Solo puede haber **un turno abierto por terminal**. Si otro cajero ya abrió
        esa caja, la app mostrará un error.
    - El monto inicial puede ser 0 si empiezas sin efectivo.
    - Solo se permiten **terminales activos** (los dados de baja no aparecen en
        el selector).

## Resultado esperado

- La app muestra un snack de éxito: "Caja abierta".
- En el menú lateral, la sección **Caja** se habilita para cobrar.
- El número de turno se muestra en la cabecera de la pantalla **Caja** (formato
    `{código_terminal}-{yyyyMMdd}-{secuencial}`).

## Errores frecuentes

| Mensaje | Causa | Solución |
|---|---|---|
| "El terminal ya tiene una caja abierta" | Otro turno activo | Pide al otro cajero que cierre su turno. |
| "Terminal no disponible" | El terminal está inactivo | Contacta al administrador para activarlo. |
| "No tienes permisos" | Tu rol no puede abrir caja | Solicita el módulo `OPCIONES_CAJA`. |

## Buenas prácticas

- Realiza la apertura al **comienzo exacto** de tu turno.
- Si el sistema te pidió cerrar la caja anterior y la dejaste abierta, ciérrala
    primero y luego abre la nueva.
- Anota el **monto inicial** en tu cuaderno o sistema paralelo para futuras
    auditorías.