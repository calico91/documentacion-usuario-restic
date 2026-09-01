# Cierre de caja (arqueo)

Al final del turno, debes **cerrar la caja**. El sistema realiza un arqueo
automático comparando lo declarado con lo esperado.

**Rol requerido:** Cajero, Administrador.

## Procedimiento

1. Asegúrate de haber **registrado todos los egresos** del turno.
2. Abre el menú lateral → **Opciones de caja** → **Cierre de caja**.

![Menú cierre](img/close-shift-menu.png)

3. La app muestra el **monto inicial** del turno y otra información básica.
4. **Cuenta el efectivo físico** que tienes en la gaveta.
5. Escribe el **monto declarado** en el campo "Efectivo en caja".
6. (Opcional) Escribe **observaciones** (por ejemplo, "Faltante por error en
    vuelto").
7. Pulsa **Cerrar caja**.
8. La app muestra un **modal de confirmación** con el monto declarado que
    acabas de escribir. Revisa que coincida con el efectivo contado en la gaveta.
    - Pulsa **Sí, Cerrar Caja** para confirmar y finalizar el turno.
    - Pulsa **Cancelar** (o fuera del modal) para volver sin cerrar; podrás
      editar el monto si necesitas ajustar.

![Formulario de cierre](img/close-shift.png)
![Confirmación de cierre](img/close-shift-confirm.png)

## Resultado del arqueo

Al cerrar, la app muestra un modal con:

- **Efectivo esperado** — calculado por el sistema:
    `monto_inicial + ventas_en_efectivo − egresos_en_efectivo`
- **Efectivo declarado** — el monto que escribiste.
- **Diferencia** — puede ser:
    - **0** → la caja **cuadró** (verde).
    - **Positiva** → **sobrante** (verde oscuro).
    - **Negativa** → **faltante** (rojo).

![Resultado del arqueo](img/close-shift-result.png)

!!! tip "Sobrantes y faltantes"
    - **Sobrante**: hay más efectivo en la gaveta del que el sistema esperaba.
        Común por errores en vueltos.
    - **Faltante**: hay menos efectivo del esperado. Común por errores en
        cobros, olvidos de egresos o robos.
    - Investiga cualquier **faltante significativo** antes de cerrar.

## Estado del turno

Tras el cierre, el turno pasa a estado **CLOSED**. Aparece en la sección
**Cierres pendientes** para que el administrador lo concilie.

## Detalles del cálculo

El sistema calcula el resumen del turno con:

- **Total transacciones** (ventas + reembolsos).
- **Total ventas** (solo SALE COMPLETED).
- **Total propinas**.
- **Egresos en efectivo** vs **egresos por banco**.
- **Resumen por método de pago** (efectivo, tarjeta, QR, transferencia, vale).

![Resumen del turno](img/shift-summary.png)

## ¿Puedo reabrir un turno cerrado?

**No.** Un turno cerrado es inmutable. Si necesitas correcciones:

1. El administrador puede **revertir el cierre** desde el backend, o
2. Crea un nuevo turno con el ajuste correspondiente (egreso o nuevo ingreso).

## Buenas prácticas

- Cierra la caja **al final exacto del turno**, no antes ni después.
- No postergues el cierre si hay faltante: repórtalo y registra una observación.
- Antes de cerrar, **verifica que la impresora** haya impreso todos los tickets
    pendientes.