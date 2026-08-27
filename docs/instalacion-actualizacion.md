# Instalación y actualización

## Instalar la app por primera vez

La app **Restic** se distribuye como un archivo `.apk` desde el área de descargas
del equipo de soporte o desde la tienda interna de tu organización.

1. Abre el enlace de descarga en tu dispositivo Android.
2. Si el sistema lo pide, autoriza la instalación desde esta fuente:
    **Ajustes → Aplicaciones → Acceso especial → Instalar apps desconocidas**.
3. Abre el archivo `.apk` descargado y pulsa **Instalar**.
4. Al finalizar, pulsa **Abrir** para iniciar la app.

!!! tip "Consejo"
    Si tu organización usa Google Play o un MDM interno, también puedes buscar
    "Restic" en la tienda.

## Actualizar la app

Restic puede forzar la actualización cuando hay cambios importantes:

### Actualización automática

1. Cuando inicies la app, esta consulta la versión mínima requerida al servidor.
2. Si la versión instalada es **inferior** a la requerida, la app abre
    automáticamente la pantalla de **Actualización obligatoria**.

![Pantalla de actualización obligatoria](img/app-update.png)

3. Pulsa **Abrir tienda** para ir a la página de descarga.
4. Descarga e instala la nueva versión.
5. Vuelve a abrir la app y pulsa **Reintentar** si la pantalla persiste.

!!! warning "Importante"
    No podrás usar la app hasta que la versión instalada sea igual o superior a
    la versión mínima requerida.

### Actualización manual (cuando la app lo permite)

1. Abre la tienda o el enlace de descarga.
2. Instala la versión más reciente sobre la actual (los datos se conservan).
3. Abre la app; si ves la pantalla de actualización, pulsa **Reintentar**.

## Ver la versión instalada

La versión actual se muestra en la esquina inferior de la **pantalla de inicio de
sesión**, por ejemplo `v2.0.8+20`.

![Versión en login](img/login-version.png)