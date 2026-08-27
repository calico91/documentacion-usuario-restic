# Manual de Usuario — Restic

Documentación de usuario de la aplicación móvil **Restic**, sistema POS para
restaurantes y heladerías.

Sitio generado con [MkDocs Material](https://squidfunk.github.io/mkdocs-material/).

## Vista local

### Requisitos previos

Necesitas **Python 3.10+** y **pip**. En Windows, si no tienes Python instalado,
puedes instalarlo con `winget`:

```bash
winget install Python.Python.3.12
```

!!! warning "Importante"
    Tras instalar Python, **cierra y reabre la terminal** para que `pip` entre
    en el PATH.

Verifica la instalación:

```bash
python --version
pip --version
```

### Instalar MkDocs Material

Opción recomendada — **entorno virtual aislado** (no ensucia el Python del
sistema):

```bash
python -m venv .venv
.venv\Scripts\activate          # Windows (en bash: source .venv/Scripts/activate)
pip install mkdocs-material
```

Opción rápida — **instalación global**:

```bash
pip install mkdocs-material
```

### Levantar el servidor de vista previa

```bash
mkdocs serve
```

Abre `http://localhost:8000` en el navegador. Para detener el servidor pulsa
`Ctrl + C`.

!!! tip "Con entorno virtual"
    Si usaste la opción de venv, recuerda **activarlo** (`.venv\Scripts\activate`)
    cada vez que abras una terminal nueva antes de ejecutar `mkdocs serve`.

## Despliegue

El workflow de GitHub Actions (`.github/workflows/deploy.yml`) publica automáticamente
el sitio en **GitHub Pages** en cada push a `main`.

Configurar en GitHub: `Settings → Pages → Source: GitHub Actions`.

## Cómo contribuir

Lee [CONTRIBUTING.md](CONTRIBUTING.md) antes de añadir o modificar una sección.