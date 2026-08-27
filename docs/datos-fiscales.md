# Datos fiscales

Configura los **datos fiscales** del establecimiento, requeridos para la
facturación electrónica (DIAN en Colombia).

**Rol requerido:** Administrador.

## Pantalla principal

Menú lateral → **Datos fiscales**.

![Datos fiscales](img/fiscal-data.png)

Solo puede haber **un registro de datos fiscales activo** por sucursal. La
pantalla carga el activo, o permite crear uno si no existe.

## Campos del formulario

### Información del establecimiento

- **Razón social** (obligatorio) — nombre legal del establecimiento.
- **NIT** (obligatorio) — número de identificación tributaria.
- **Dígito de verificación** (obligatorio) — un dígito calculado a partir del
    NIT.
- **Dirección** (obligatorio).
- **Ciudad** (obligatorio).
- **Departamento** (obligatorio).
- **Régimen tributario** — selecciona:
    - `SIMPLE` — régimen simple de tributación.
    - `ORDINARIO` — régimen ordinario.
    - `NO_RESPONSABLE_IVA` — no responsable de IVA.

### Resolución DIAN

- **Número de resolución** (obligatorio).
- **Fecha de inicio de resolución** (obligatorio).
- **Fecha de fin de resolución** (obligatorio).
- **Prefijo de factura** (obligatorio) — texto corto (ej. "FV").
- **Rango de numeración desde** (obligatorio).
- **Rango de numeración hasta** (obligatorio).

### Contacto

- **Email** (obligatorio).
- **Teléfono** (opcional).
- **Sitio web** (opcional).

![Formulario fiscal](img/fiscal-data-form.png)

!!! warning "Importante"
    - La **fecha de fin de resolución** debe ser **posterior** a la fecha de
        inicio.
    - El rango de numeración **desde** debe ser **menor** que el rango **hasta**.
    - Estos datos se usan para **todas las facturas** que emitas. Verifica con
        tu contador antes de guardar.

## Guardar datos fiscales

1. Completa todos los campos obligatorios.
2. Pulsa **Guardar**.

Si ya existía un registro activo, se actualiza el actual.

## Historial de datos fiscales

El sistema conserva el **historial completo** de todos los registros fiscales
que hayas tenido, por si necesitas consultarlos (por ejemplo, para una factura
emitida bajo una resolución anterior).

Para acceder al historial, contacta al administrador del sistema.

## Efecto en la facturación

Al generar una factura, el sistema:

1. Toma los **datos fiscales activos** de la sucursal.
2. Asigna un **número de factura** correlativo dentro del rango autorizado:
    `INV-{yyyyMMdd}-{6 dígitos}`.
3. Incluye todos los datos en el PDF/XML de la factura.
4. Si envías la factura por email, el remitente es el email registrado.

!!! warning "Cambio de resolución"
    Cuando cambies de resolución DIAN:
    1. Crea un nuevo registro fiscal (no edites el actual).
    2. El sistema desactiva el antiguo y activa el nuevo.
    3. Las nuevas facturas usarán el rango nuevo.
    4. Las facturas pasadas conservan el rango con que fueron emitidas.

!!! tip "Soporte del contador"
    Si tienes dudas sobre qué régimen tributario aplica o cómo diligenciar la
    resolución, consulta con tu contador. Estos datos son críticos para la
    validez legal de las facturas.