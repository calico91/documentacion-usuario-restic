# Cómo contribuir al manual

Este manual se mantiene con **docs-as-code**: cada sección es un archivo Markdown en
`docs/`, registrado en el `nav:` de `mkdocs.yml`. Está versionado en git, se revisa
por PR y se publica con MkDocs Material.

## Estructura

```
docs/
├── img/          # capturas de pantalla (referenciadas como ![alt](img/archivo.png))
└── *.md          # una sección por archivo
mkdocs.yml        # índice de navegación (nav:)
```

## Añadir una nueva funcionalidad

Cuando se implementa una nueva pantalla o flujo en la app móvil
(`d:\Flutter\restic-movil`), el agente debe reflejarlo aquí:

1. **Crear el archivo** `docs/<nombre-seccion>.md` (kebab-case, sin acentos).
2. **Registrarlo en `mkdocs.yml`** bajo `nav:`, en la sección temática adecuada
   (Operación diaria, Gestión de caja, Administración, Impresión, etc.).
3. **Colocar capturas** en `docs/img/` y referenciarlas como
   `![Descripción de la pantalla](img/nombre-archivo.png)`.
4. **Hacer commit** en este repo (`documentacion-usuario-restic`), independiente del
   commit en el repo del móvil.

## Modificar una sección existente

1. Editar `docs/<archivo>.md` directamente.
2. Si el cambio renombra o reordena el flujo, actualizar también el `nav:` y las
   referencias cruzadas (links `texto`](archivo.md)`).
3. Commit descriptivo.

## Plantilla por sección

Cada `.md` sigue esta estructura recomendada:

```markdown
# Título de la sección

**Objetivo:** una frase explicando qué logrará el usuario.

**Rol requerido:** Mesero / Cajero / Cocinero / Administrador (los que aplique).

## Pasos

1. Paso uno.
2. Paso dos.
3. ...

!!! tip "Consejo"
    Información útil opcional.

!!! warning "Importante"
    Advertencia o requisito.

## Resultado esperado

Qué verá el usuario al finalizar.

## Capturas

![Pantalla inicial](img/ejemplo.png)
```

## Convenciones de estilo

- **Lenguaje sencillo**, en español neutro/Colombia. Evita tecnicismos innecesarios.
- **Tiempo presente**, segunda persona del singular (*"Toca el botón..."*).
- **Pasos numerados**, cortos, uno por acción.
- **Admonitions** de MkDocs Material:
  `!!! tip` para sugerencias, `!!! warning` para avisos importantes,
  `!!! note` para aclaraciones, `!!! danger` para acciones irreversibles.
- **Imágenes**: usa PNG/JPG, ancho recomendado 360-800 px. Describe el contenido en
  el `alt` para accesibilidad.
- **Tablas** para listar permisos por rol o catálogos de opciones.
- **No enlaces externos rotos**: si referencias una sección interna, usa la forma
  `[texto](archivo.md)` (MkDocs resuelve el `.md` automáticamente).

## Validar en local antes de hacer commit

```bash
mkdocs serve            # vista previa en http://localhost:8000
mkdocs build --strict   # falla si hay enlaces rotos o warnings
```

## Versiones

- Cambios incompatibles con versiones anteriores de la app deben documentarse en la
  sección correspondiente con un bloque `!!! warning "Cambio en versión vX.Y"`.
- Si eliminas una sección, rediriige la entrada del `nav:` a la nueva sección.