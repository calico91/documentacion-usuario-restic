# Egresos de caja (salidas de dinero)

Durante el turno, puedes registrar salidas de dinero: pagos a proveedores,
gastos menores, devoluciones al cliente, etc.

**Rol requerido:** Cajero, Administrador.

## Procedimiento

1. Abre el menú lateral → **Opciones de caja** → **Egresos**.

![Menú egresos](img/expenses-menu.png)

2. Completa el formulario:
    - **Monto** — valor en pesos del egreso.
    - **Concepto** — descripción breve (ej. "Pago proveedor de gas").
    - **Referencia comprobante** — número de factura o soporte (opcional).
    - **Motivo** — selecciona de la lista desplegable:
        - Pago a proveedor
        - Gasto menor
        - Devolución a cliente
        - Caja menor
        - Mantenimiento
        - Otro
    - **Medio de pago** — selecciona:
        - **Efectivo** — sale de la gaveta.
        - **Cuenta bancaria** — no afecta la gaveta (Nequi, Bancolombia, etc.).

3. Si elegiste **Cuenta bancaria**, completa:
    - **Nombre de la cuenta** (obligatorio).
    - **Referencia bancaria** (opcional).

4. Pulsa **Registrar egreso**.

![Formulario de egreso](img/expenses-form.png)

!!! warning "Importante"
    - Solo puedes registrar egresos durante un **turno abierto**.
    - El sistema valida que tengas **suficiente efectivo en caja** cuando el
        medio es efectivo. Si no, mostrará un error.
    - Los egresos por **cuenta bancaria** no validan saldo en caja.

## Alertas automáticas

Si el egreso supera el **umbral de alerta** configurado por el administrador
(valor por defecto: $200.000), la app:

- Marca el egreso con un ícono de advertencia (⚠️).
- Lo lista en la sección **"Alertas"** del módulo de Historial para revisión.

![Egreso con alerta](img/expense-alert.png)

## Resultado esperado

- El egreso aparece inmediatamente en la pantalla de egresos.
- Se descuenta del cálculo de **efectivo esperado** al cierre de caja (si es
    efectivo).
- Aparece en el **Historial de egresos** y puede exportarse a CSV.

## Buenas prácticas

- Justifica cada egreso con una **referencia** (número de factura del proveedor,
    por ejemplo).
- Usa **motivos** claros para facilitar los reportes.
- Si la alerta salta por monto alto, asegúrate de que tienes autorización del
    administrador.

## ¿Y si me equivoqué?

Los egresos **no se editan** desde la app una vez registrados. Si necesitas
corregir uno:

1. Pide al **administrador** que lo anule manualmente desde el backend, o
2. Registra un **egreso inverso** (devolución o compensación) con el mismo
    motivo.