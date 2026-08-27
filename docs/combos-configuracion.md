# Combos

Los productos tipo **COMBO** se componen de **grupos** (categorías internas) con
**opciones** (productos seleccionables). Esta pantalla te permite crear y
gestionar esa estructura.

**Rol requerido:** Administrador.

## Conceptos

- **Grupo** — categoría lógica dentro del combo (ej. "Proteína", "Acompañamiento").
- **Opción** — un producto que el cliente puede elegir dentro del grupo.
- **Mínimo y máximo** — cuántas opciones debe/debe poder elegir el cliente.
- **Requerido** — si el grupo es obligatorio.
- **Precio adicional** — algunas opciones pueden sumar al precio base del combo.

## ¿Dónde se configura?

1. Menú lateral → **Menú**.
2. Selecciona la categoría del combo.
3. Toca el producto tipo **COMBO**.
4. En el menú emergente, pulsa **Administrar combo**.

![Administrar combo](img/combo-admin.png)

## Pantalla de administración de combo

![Editor de combo](img/combo-editor.png)

- Muestra los grupos existentes con sus opciones.
- Para cada grupo puedes:
    - Agregar opciones.
    - Quitar opciones.
    - Activar o desactivar opciones.
    - Cambiar el precio adicional de una opción.

## Agregar una opción a un grupo

1. Selecciona el grupo al que quieres agregar.
2. Pulsa **Agregar opción**.
3. Busca y selecciona el producto que será opción.
4. Define el **precio adicional** (puede ser 0).
5. Pulsa **Guardar**.

!!! tip "Productos opción"
    - Un producto opción puede ser **SIMPLE** o un producto marcado como
        **"Solo opción de combo"**.
    - Los productos opción no aparecen en el catálogo principal al tomar
        pedidos; solo se ven al armar el combo.

## Quitar o desactivar una opción

- **Quitar**: elimina la opción del grupo (no se puede deshacer).
- **Desactivar**: la opción queda pero no se ofrece al cliente. Útil para
    opciones estacionales o sin stock temporal.

!!! note "Stock temporal"
    Para manejar opciones sin stock sin eliminarlas, **desactívalas**. Así
    conservas el historial y puedes reactivarlas cuando vuelvan a estar
    disponibles.

## Editar el precio adicional de una opción

1. Toca la opción en el editor.
2. Cambia el campo **Precio adicional**.
3. Pulsa **Guardar**.

## Validaciones

- Un combo debe tener **al menos un grupo** para poder pedirse.
- Cada grupo debe tener **al menos una opción** (no se permite eliminar la
    última opción de un grupo).
- Los grupos con `mínimo > 0` son obligatorios al armar el combo.

## Ejemplo: Combo Almuerzo

| Grupo | Requerido | Mín | Máx | Opciones |
|---|:---:|:---:|:---:|---|
| Proteína | ✅ | 1 | 1 | Pollo +$0, Carne +$2.000, Pescado +$3.000 |
| Acompañamiento | ✅ | 1 | 2 | Papas +$0, Arroz +$0, Ensalada +$1.500 |
| Bebida | ❌ | 0 | 1 | Gaseosa +$0, Jugo +$1.000, Agua +$0 |

Al armar este combo, el cliente:

1. Elige **1 proteína** (obligatorio).
2. Elige **1 o 2 acompañamientos** (obligatorio, mínimo 1).
3. Opcionalmente elige 1 bebida (no obligatoria).
4. El precio del combo es: `precio_base + (adicionales_de_proteína + adicionales_de_acompañamiento + adicional_de_bebida)`.

## Buenas prácticas

- Nombra los grupos de forma clara para el cliente (ej. "Proteína" en vez de
    "Grupo 1").
- Usa **adicionales** solo cuando quieras cobrar extra (ej. proteína
    premium).
- Marca como **desactivadas** las opciones que no ofrezcas temporalmente.