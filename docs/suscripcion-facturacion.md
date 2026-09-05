# Suscripción y facturación

Gestiona la **suscripción** de tu negocio con Restic: prueba gratuita,
facturación por aniversario del trial y facturas del servicio.

**Rol requerido:** Administrador.

!!! tip "Qué es la suscripción de Restic"
    Restic cobra mensualmente según el uso real del sistema: un monto base
    más un valor extra por cada usuario activo y cada sucursal adicional por
    encima de lo incluido en tu plan. La facturación se alinea al **día del
    mes en que termina tu prueba gratuita**, así que cada negocio tiene su
    propio día de facturación y siempre paga **por adelantado** el mes que
    está por comenzar.

## Antes de empezar: inicia tu prueba gratuita

La primera vez que un **Administrador** inicia sesión en Restic, el sistema
le pide **iniciar la prueba gratuita** de 14 días. Hasta que se inicie la
prueba, ningún miembro del negocio puede acceder al sistema (red de
seguridad para que ningún negocio use Restic sin activar la suscripción).

**Objetivo:** activar el período de prueba gratuito y arrancar el ciclo de
facturación del negocio.

**Rol requerido:** Administrador.

### Pasos

1. Inicia sesión como Administrador.
2. La pantalla inicial muestra el botón **Iniciar prueba gratis**.
3. Pulsa el botón.
4. Verás un mensaje de confirmación: *"Tienes 14 días de prueba. La
   primera factura se genera el día que termine la prueba y las siguientes
   ese mismo día de cada mes."*
5. Automáticamente accederás al sistema por **14 días sin costo**.

### Resultado esperado

- El negocio puede usar Restic durante 14 días sin pagar.
- El **día que termina la prueba** el sistema genera la primera factura
  por el mes entrante y la suscripción pasa a **Activa**.

!!! warning "Importante"
    - El período de prueba **no se renueva**: cuando termina, la suscripción
        pasa a **Activa** y se empieza a facturar el mismo día.
    - El **día de facturación** se fija al día en que termina la prueba y se
        mantiene igual para siempre (aniversario). Si el trial termina el 20
        de agosto, las facturas se emiten los días 20 de cada mes.
    - Si el negocio deja de usar el sistema por más de un mes, al volver
        recibe una sola factura por el ciclo nuevo (no se cobran meses
        muertos).

## Ver tu suscripción actual

Menú lateral → **Configuración** → **Suscripción y Facturación**.

La pantalla principal muestra el **estado actual**:

- **Período de prueba** (naranja) — cuántos días te quedan y cuándo termina.
- **Suscripción activa** (verde) — **próxima fecha de facturación** (el día
  del mes en que terminó tu prueba).
- **Suscripción suspendida** (rojo) — el servicio está cortado por falta
  de pago. Contacta al equipo de Restic para registrar el pago.

![Suscripción](img/suscripcion-estado.png){ loading=lazy }

!!! info "Banner de estado en el inicio"
    Cuando el período de prueba está por terminar (naranja) o la suscripción
    está suspendida (rojo), aparece un **banner en la pantalla de inicio**
    de la app que te lleva directo a esta pantalla con un toque.

## Entender la facturación

El sistema genera **una factura al mes** automáticamente el **día del mes
en que terminó tu prueba** (tu día de aniversario), cubriendo el mes
entrante. Por ejemplo, si tu prueba terminó el **20 de agosto**, la primera
factura se emite el **20 de agosto** cubriendo del 20 de agosto al 20 de
septiembre, y las siguientes el **20 de septiembre**, **20 de octubre**, y
así sucesivamente.

### Cómo se calcula el monto

| Concepto | Valor |
|---|---|
| Precio base del plan | $30.000 COP / mes (plan Standard) |
| Sucursales incluidas | 1 |
| Usuarios activos incluidos | 2 |
| Sucursal adicional | + $15.000 COP / mes |
| Usuario activo adicional | + $5.000 COP / mes |

!!! info "Qué es un usuario activo"
    Un usuario activo es cualquier persona que haya hecho al menos una
    operación dentro del ciclo. Al facturar, el sistema **reinicia** los
    contadores y empieza el nuevo ciclo en cero. El usuario vuelve a contar
    cuando ingresa de nuevo en el siguiente ciclo.

### Ejemplo

El negocio *"Antojitos"* usa el plan Standard, tiene 1 sucursal y durante
el primer ciclo ingresaron **3 usuarios** distintos al sistema:

- Base: $30.000
- Usuarios extra: 1 (tercer usuario, 2 están incluidos) → + $5.000
- Sucursales extra: 0 (1 incluida) → + $0

**Primera factura: $35.000**, emitida el 20 de agosto (día en que terminó
su prueba) cubriendo del 20 de agosto al 20 de septiembre.

En el siguiente ciclo solo ingresaron **2 usuarios**, así que la factura
del 20 de septiembre es solo el base: **$30.000**.

### Caso especial: trial terminado sobre el 29-31

Si tu prueba termina un día **29, 30 o 31**, tu día de facturación se
**ajusta al 28** para evitar que las facturas salten de mes (febrero es
más corto). Por ejemplo, prueba que termina el **31 de enero** → facturas
los días **28 de febrero, 28 de marzo, 28 de abril**, etc.

## Ver y pagar facturas

En la pantalla de Suscripción, debajo del estado actual aparece la lista
de **Facturas** con la siguiente información por factura
(se muestran las últimas 12 facturas — un año de historial):

- **Monto total** ($)
- **Periodo facturado** (fecha de inicio → fecha de fin) — siempre el
  mes entrante.
- **Fecha de vencimiento** (5 días después de emitida)
- **Estado**: Pendiente (naranja) o Pagada (verde, verificada)

!!! info "Cómo se registra el pago"
    Por ahora **no hay botón de pago en la app ni en la web** — el pago
    lo registra directamente el equipo de la plataforma en base de datos
    (script `scripts/mark_subscription_invoice_paid.sql`). Al refrescar
    la pantalla de Suscripción verás la factura como **Pagada** y, si
    la suscripción estaba suspendida, vuelve a **Activa** automáticamente.

## Suscripción suspendida

Si el flag de suspensión está activo en la plataforma y una factura queda
**vencida** sin pagar, la suscripción pasa a **Suspendida** y el servicio
se corta (HTTP 402 en todos los endpoints para todo el personal del
negocio, no solo para el administrador).

La pantalla de Suscripción muestra una vista específica con:

- Motivo de la suspensión (ej. `INVOICE_OVERDUE`).
- Botón **Ver facturas pendientes** para acceder al listado (solo
  consulta; las facturas se marcan como pagadas desde la plataforma).

Una vez registrado el pago por el equipo de la plataforma, la suscripción
vuelve automáticamente a **Activa** al refrescar la pantalla.

!!! note "Orden de cobro y suspensión"
    Si al llegar tu día de facturación tienes una factura anterior
    **vencida** y la suspensión está activada, la suscripción se suspende
    **antes** de emitir la nueva factura del ciclo entrante. No se cobra
    el nuevo ciclo hasta que se registre el pago de la factura vencida.

## Resumen rápido

| Acción | Ruta |
|---|---|
| Iniciar prueba gratuita | Tras login admin, botón en pantalla inicial |
| Ver estado de mi suscripción | Menú lateral → Configuración → Suscripción y Facturación |
| Ver facturas | Misma pantalla, sección "Facturas" |
| **Ver detalle de una factura** | **Toca la factura en la lista** |
| Marcar factura como pagada | Lo hace el equipo de la plataforma (no hay botón en la app) |
| Volver de suspensión | El equipo de la plataforma registra el pago del cliente |

## Ver detalle de una factura

**Objetivo:** entender exactamente qué se está cobrando en una factura
(plan base, usuarios adicionales, sedes adicionales), con el desglose y
los nombres de las sedes y los usuarios contados en ese ciclo.

**Rol requerido:** Administrador.

### Pasos

1. Abre **Suscripción y Facturación** desde el menú lateral.
2. En la sección **Facturas**, toca la factura que quieres revisar.
3. Se abre un diálogo con el detalle completo:

   ```
   Detalle de factura
   ─────────────────────────────
   Periodo:  20/08/2026 → 20/09/2026
   Vence:    25/08/2026
   Emitida:  20/08/2026
   Estado:   Pendiente

   Desglose
   ─────────────────────────────
   Plan base (Standard)              $30.000
   Usuarios adicionales (1)          $ 5.000
   Sedes adicionales (0)             $ 0
   ─────────────────────────────
   TOTAL                              $35.000

   Sedes:  Sede Centro
   Usuarios activos del ciclo:  Laura Pérez, Jhon Gómez, Carolina Ruiz
   ```

!!! tip "Cómo se interpreta el desglose"
    - **Plan base**: monto fijo del plan (mensual o anual).
    - **Usuarios adicionales**: usuarios activos por encima de los
        incluidos en el plan (en el ejemplo, 1 adicional = 1 × $5.000).
    - **Sedes adicionales**: sucursales activas por encima de las
        incluidas en el plan.
    - **Sedes / Usuarios activos del ciclo**: lista con los nombres
        contados para ese cobro. Una sede desactivada no aparece ni se
        cobra; un usuario que no hizo ninguna petición en el ciclo tampoco.

!!! info "Facturas generadas antes del detalle"
    Las facturas antiguas (sin los campos de desglose y nombres) muestran
    solo el monto total y el mensaje *"Información detallada no disponible
    para esta factura"*. Esto se resuelve automáticamente a partir de la
    siguiente factura generada.

### Resultado esperado

Entiendes exactamente qué se está cobrando y puedes verificar que
coincide con el uso real del negocio en el ciclo facturado.
