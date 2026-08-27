# Cierres pendientes y conciliación

Una vez que el cajero cierra una caja, el turno pasa a estado **CLOSED**. La
**conciliación** es el proceso administrativo de revisar y aprobar el cierre.

**Rol requerido:** Solo `SUPER` y `ADMINISTRADOR` (conciliación).

## Pantalla Cierres pendientes

Abre el menú lateral → **Opciones de caja** → **Cierres pendientes**.

![Cierres pendientes](img/pending-closes.png)

La pantalla tiene dos secciones:

- **Sin cerrar** — turnos en estado **OPEN** (no cerrados por el cajero).
- **Pendientes de conciliar** — turnos en estado **CLOSED** que requieren
    aprobación.

### Ver el arqueo de un cierre

1. Toca sobre el turno en la lista.
2. La app abre un modal con el resumen completo (similar al del cierre):
    - Monto inicial.
    - Total ventas.
    - Egresos totales (efectivo y bancarios).
    - Propinas.
    - Efectivo disponible.
    - Efectivo esperado, declarado y diferencia.
    - Desglose por método de pago.

![Arqueo de cierre](img/close-detail.png)

## Conciliar un cierre

1. Toca el turno en **Pendientes de conciliar**.
2. Revisa el arqueo. Si todo está correcto, pulsa **Conciliar**.
3. Confirma la acción.

Tras conciliar, el turno pasa a estado **RECONCILED** y desaparece de la lista
de pendientes.

!!! warning "Importante"
    - La conciliación es **inmediata** y no se puede deshacer desde la app.
    - Si detectas un error (por ejemplo, un faltante considerable), no concilies
        y repórtalo al cajero o al equipo de soporte antes de aprobar.

!!! note "Permisos del cajero"
    Los cajeros ven en esta misma pantalla solo **sus propios turnos**. No ven
    los turnos de otros cajeros. Solo `SUPER` y `ADMINISTRADOR` ven todos.

## Buenas prácticas de conciliación

- Revisa los **faltantes y sobrantes** antes de aprobar.
- Verifica que las **alertas de egreso** (montos altos) estén justificadas.
- Compara el **efectivo esperado vs declarado** con el cuaderno o sistema
    paralelo del cajero.
- Si un turno tiene varios **reembolsos grandes**, valida que estén autorizados.

## Estados de un turno

| Estado | Significado | Quién puede verlo |
|---|---|---|
| `OPEN` | Caja abierta, en operación. | Cajero dueño + admins |
| `CLOSED` | Caja cerrada, pendiente de conciliación. | Admins (en Cierres pendientes) |
| `RECONCILED` | Caja cerrada y aprobada por un admin. | Admins (histórico) |