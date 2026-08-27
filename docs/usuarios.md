# Usuarios

El módulo **Usuarios** gestiona las cuentas que pueden iniciar sesión en el
sistema: alta, edición, desactivación, restablecimiento de contraseña.

**Rol requerido:** Solo `SUPER` y `ADMINISTRADOR`.

## Pantalla principal

Menú lateral → **Usuarios**.

![Pantalla Usuarios](img/users.png)

- Lista todos los usuarios de la sucursal.
- Buscador por nombre, usuario o email.
- Botón flotante **+** para crear un usuario.

## Crear un usuario

1. Pulsa el botón **+**.
2. Completa el formulario:
    - **Username** (obligatorio, único global; en minúsculas).
    - **Primer nombre** (obligatorio).
    - **Segundo nombre** (opcional).
    - **Primer apellido** (obligatorio).
    - **Segundo apellido** (opcional).
    - **Móvil** (obligatorio, único global).
    - **Email** (opcional, único global).
    - **Contraseña** (obligatoria en creación; mínimo 6 caracteres).
    - **Activo** (switch; activado por defecto).
    - **Roles** — selecciona uno o más de los 5 disponibles:
        - `SUPER`
        - `ADMINISTRADOR`
        - `MESERO`
        - `COCINERO`
        - `CAJERO`
3. Pulsa **Guardar**.

![Formulario de usuario](img/user-form.png)

!!! note "Asignación de módulos"
    Los módulos visibles para el usuario se calculan automáticamente a partir de
    sus roles (ver [Roles y permisos](roles-permisos.md)).

!!! warning "Importante"
    - El username, móvil y email son únicos en todo el sistema (no solo en la
        sucursal).
    - La contraseña inicial es temporal; el usuario deberá cambiarla al primer
        inicio de sesión.

## Editar un usuario

1. Toca el usuario en la lista.
2. Modifica los campos.
3. Pulsa **Guardar**.

!!! note "Contraseña"
    En edición, el campo de contraseña está vacío. Si no lo tocas, la contraseña
    actual se mantiene.

## Activar / desactivar un usuario

1. En la lista de usuarios, usa el **switch** de cada fila.
2. Confirma el cambio.

![Switch activo/inactivo](img/user-toggle.png)

!!! warning "Importante"
    - **No puedes desactivarte a ti mismo**.
    - Un usuario desactivado **no puede iniciar sesión**.
    - Los pedidos y registros históricos se conservan (el usuario sigue
        apareciendo como "creado por" en pedidos antiguos).

## Restablecer contraseña

1. Toca el usuario → **Restablecer contraseña** (icono de llave).
2. Confirma la acción.
3. La app muestra una **contraseña temporal** (una sola vez). Cópiala y
    compártela con el usuario por un canal seguro.
4. Al iniciar sesión, el sistema le pedirá cambiarla.

![Restablecer contraseña](img/reset-password.png)

!!! tip "Consejo de seguridad"
    Envía la contraseña temporal por un canal separado del aviso (por ejemplo,
    por WhatsApp di el aviso por correo, y viceversa). Así reduces el riesgo si
    uno de los canales está comprometido.

## Eliminar un usuario

Solo `SUPER` puede eliminar usuarios (no solo desactivarlos).

1. Toca el usuario → **Eliminar** (icono papelera).
2. Confirma.

!!! warning "Restricción"
    - No puedes eliminarte a ti mismo.
    - Si el usuario tiene actividad reciente (transacciones, pedidos), el
        sistema puede impedir la eliminación. En ese caso, **desactívalo** en
        su lugar.

## Cambiar mi propia contraseña

Si eres tú quien quiere cambiar su contraseña, ve a la sección
[Cambiar contraseña](cambiar-contrasena.md).