# Reportes de ventas

El módulo **Reportes** permite analizar las ventas de la sucursal por distintos
criterios: rango de fechas, turno, fecha exacta, etc.

**Rol requerido:** Administrador. Los cajeros ven solo sus propios turnos.

## Pantalla principal

Menú lateral → **Reportes**.

![Reportes](img/reports.png)

Selecciona primero el **tipo de reporte**:

1. **Por rango de fechas** — agrupa todas las ventas entre dos fechas (día
    completo).
2. **Por fecha-hora exacta** — para turnos nocturnos que cruzan la medianoche.
3. **Por turno específico** — reporte detallado de un turno (necesita su ID).
4. **Por fecha de apertura de turno(s)** — incluye todos los turnos abiertos en
    una fecha.

## Configurar el reporte

Una vez elegido el tipo, completa los selectores:

- **Rango de fechas**: desde / hasta.
- **Fecha-hora exacta**: desde / hasta (con hora).
- **Turno específico**: ID del turno (lo encuentras en **Cierres pendientes**
    o **Historial de turnos**).
- **Fecha de apertura**: solo una fecha.

## Tarjetas de resumen

Al ejecutar el reporte, la app muestra:

- **Transacciones** — número total de transacciones del período.
- **Ventas** — suma total de ventas (sin propinas ni cargos).
- **Propinas** — suma total de propinas.
- **Ingreso bruto** — ventas + propinas.

![Resumen de reporte](img/reports-summary.png)

## Desglose por medios de pago

Una sección muestra, para cada método de pago:

- Número de transacciones.
- Porcentaje del total.
- Monto total.

![Desglose por medios](img/reports-payment-breakdown.png)

## Resumen por cajero

Si el reporte incluye varios turnos, muestra también el detalle por cada cajero:

- Cajero.
- Número de transacciones.
- Ventas.
- Propinas.

![Resumen por cajero](img/reports-by-cashier.png)

## Reporte de un turno específico

Si elegiste "Por turno específico", además de las tarjetas verás la **tarjeta
de información del turno**:

- Número de turno.
- Cajero.
- Terminal.
- Estado (OPEN / CLOSED / RECONCILED).
- Fecha y hora de apertura / cierre.

![Info del turno](img/reports-shift-info.png)

## Diferenciación por rol

- **Cajero**: solo puede ver reportes de **sus propios turnos** (selector
    "Por turno" está limitado a los turnos donde fue cajero).
- **Administrador**: ve todos los turnos y reportes de la sucursal.

## Tipos de transacciones incluidas

Solo se incluyen en el reporte las transacciones:

- **Tipo**: `SALE` (ventas) y `REFUND` (reembolsos).
- **Estado**: `COMPLETED` (completadas).

Las transacciones canceladas (`CANCELLED`) o pendientes (`PENDING`) **no**
aparecen.

## Buenas prácticas

- Genera reportes al **final del día** para hacer cierre diario.
- Para auditoría mensual, usa **rango de fechas** con cuidado si tu local opera
    en turnos nocturnos (puede haber ventas del turno de noche que caigan en
    dos días calendario distintos).
- Exporta los datos regularmente y guárdalos en un sistema de respaldo.