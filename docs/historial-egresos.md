# Historial de egresos

Esta pantalla muestra todos los egresos registrados en la sucursal, con
filtros y exportación a CSV.

**Rol requerido:** Cajero (solo ve los suyos), Administrador (ve todos).

## Acceder al historial

Menú lateral → **Opciones de caja** → **Historial de egresos**.

![Historial de egresos](img/withdrawals-history.png)

## Filtros

En la parte superior puedes filtrar por:

- **Rango de fechas** — desde/hasta.
- **Motivo** — pago a proveedor, gasto menor, devolución, etc.
- **Usuario** — solo disponible para administradores; te permite filtrar los
    egresos de un cajero específico.

## Tarjeta de egreso

Cada egreso muestra:

- **Monto** (en rojo).
- **Medio** (chip: efectivo o banco).
- **Concepto**.
- **Motivo**.
- **Turno** en el que se registró.
- **Registrado por** (usuario).
- **Referencia** de comprobante y bancaria (si aplica).
- **Fecha y hora**.
- ⚠️ **Icono de alerta** si superó el umbral configurado.

## Exportar a CSV

1. Aplica los filtros que quieras (opcional, exporta lo filtrado).
2. Pulsa el botón **Exportar CSV** (icono de descarga).
3. La app genera un archivo `egresos-{fecha}.csv` con todas las columnas
    visibles.
4. Elige con qué app abrirlo (correo, Drive, WhatsApp, etc.) para compartirlo
    o guardarlo.

![Exportar CSV](img/export-csv.png)

!!! note "Formato del CSV"
    - Codificación UTF-8 con BOM (compatible con Excel).
    - Separador: coma.
    - Columnas: fecha, monto, medio, motivo, concepto, referencia comprobante,
        cuenta bancaria, referencia bancaria, usuario, turno, alerta.

## Detalle por egreso

Toca un egreso para ver el detalle completo y, si lo necesitas, el turno al que
pertenece.

## Diferenciación por rol

- **Cajero**: solo ve los egresos que él mismo registró durante sus turnos.
- **Administrador**: ve todos los egresos de la sucursal.

!!! tip "Conciliación"
    Este historial es la fuente de información principal para conciliar los
    egresos contra el flujo de caja esperado al final del turno.