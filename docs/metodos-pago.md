# Métodos de pago

Configura qué **métodos de pago** están disponibles en tu sucursal y cómo se
muestran al cajero.

**Rol requerido:** Administrador.

## Métodos disponibles en Restic

| Método | Código | Descripción |
|---|---|---|
| Efectivo | `CASH` | Pago en efectivo (afecta la gaveta). |
| Tarjeta de crédito | `CREDIT_CARD` | Tarjeta de crédito (Visa, Mastercard, etc.). |
| Tarjeta de débito | `DEBIT_CARD` | Tarjeta de débito. |
| QR / Nequi / Daviplata | `QR` | Pagos por código QR o billeteras móviles. |
| Transferencia bancaria | `BANK_TRANSFER` | Transferencias a cuenta bancaria. |
| Vale | `VOUCHER` | Vales, bonos o tickets canjeables. |

Por defecto, los seis métodos están creados en cada sucursal; **VOUCHER** inicia
desactivado.

## Pantalla de configuración

Menú lateral → **Métodos de pago**.

![Métodos de pago](img/payment-methods.png)

- Lista los métodos en el orden configurado (`displayOrder`).
- Cada método muestra: nombre, estado activo/inactivo y orden.

## Editar un método

1. Toca el método.
2. Modifica los campos:
    - **Nombre a mostrar** (`displayName`) — cómo aparece en la pantalla de
        cobro. Por ejemplo, en vez de "BANK_TRANSFER" puedes poner
        "Transferencia Bancolombia".
    - **Activo** — si está desactivado, no aparece en el selector al cobrar.
    - **Orden** — controla la posición en la lista (menor a mayor).
3. Pulsa **Guardar**.

![Editar método](img/payment-method-form.png)

!!! warning "Importante"
    - **No puedes crear ni eliminar métodos**, solo editar la configuración de
        los existentes.
    - Desactivar un método **no afecta** transacciones pasadas ya registradas
        con ese método.

## ¿Cómo afectan los métodos al cobro?

Al cobrar un pedido, el selector de métodos de pago solo muestra los métodos
**activos**. Esto permite, por ejemplo:

- Activar QR solo cuando tengas el datafono/QR configurado.
- Desactivar VOUCHER si no aceptas vales.
- Personalizar el nombre del método de transferencia para que el cajero y el
    cliente lo identifiquen claramente.

## Cambiar el orden

Si quieres que un método aparezca primero en el selector (por ejemplo, "Efectivo"
siempre arriba):

1. Edita el método.
2. Baja el campo **Orden** a un número menor que los demás.
3. Guarda.

Los cambios se reflejan inmediatamente en la próxima apertura del modal de
cobro (los cajeros no necesitan reiniciar sesión).