# Crear Documentación con Sphinx

Aquí dejo mis notas y pasos para crear documentación profesional para mis proyectos usando Sphinx y VSCode.

## 1. Crear el Proyecto de Documentación

Primero, necesito crear la estructura base del proyecto.

### Comando de Inicio

En la terminal, dentro de la carpeta de mi proyecto, ejecuto:

```bash
sphinx-quickstart

```

El asistente me hará algunas preguntas. Respondo así:

<li> Separate source and build directories (y/n): y (Esto es ideal para mantener mis archivos de origen limpios y separados de los archivos generados).

<li>Project name: Mi Proyecto

<li>Author name(s): Tu Nombre

<li>Project language [en]: es (para que la documentación esté en español).

Al terminar, veré dos nuevas carpetas en mi proyecto: source (donde escribiré) y build (que estará vacía por ahora).

---

## 2. Personalizar la Configuración en VSCode
Para usar el tema que instalé y otras funciones, abro el archivo **source/conf.py** en VSCode.

Cambiar el Tema HTML
Busco la línea que define el tema HTML (html_theme) y la cambio a:

Python

**html_theme = 'sphinx_rtd_theme'**

Habilitar autodoc
Si quiero generar documentación automáticamente a partir de mi código Python, busco la lista de extensiones (extensions) y agrego **'sphinx.ext.autodoc'**:

**Python**
```
extensions = [
    'sphinx.ext.autodoc',
]
```
Nota: autodoc lee las descripciones (docstrings) de mis funciones y clases y las convierte en documentación.

---

### 3. Escribir y Previsualizar la Documentación
Sphinx usa el formato reStructuredText (.rst). La extensión de VSCode me permite ver los cambios en tiempo real.

Abro el archivo **source/index.rst.** Este es el archivo principal de mi documentación.

Hago clic derecho en cualquier parte del archivo y selecciono "Open Preview".

Aparecerá un panel al lado con la vista previa. Cada vez que edito y guardo (Ctrl + S), la vista se actualizará.

Ejemplo de cómo escribir en .rst
Fragmento de código
```
.. Título de mi Proyecto
   =====================

   Este es el título principal. Usa el mismo carácter que el del subrayado para que funcione.

.. toctree::
   :maxdepth: 2
   :caption: Contenido:

   introduccion
   instalacion
   ejemplo

### Introducción
---------------
Párrafo de introducción. Puedes usar **negrita**, *cursiva*, `código` y `enlaces <https://es.wikipedia.org/wiki/Sphinx_(software_de_documentaci%C3%B3n)>`_.

### Código
---------
Para mostrar código, usa la directiva ``.. code-block::``:

.. code-block:: python

   def saludar(nombre):
       print(f"Hola, {nombre}!")
```

---

### 4. Generar los Archivos Finales
Cuando esté listo para generar mi documentación, sigo estos pasos en la terminal:

Me aseguro de estar en la raíz de mi proyecto (no en la carpeta source).

Ejecuto el comando para construir los archivos HTML:
```
En Linux/macOS:

Bash

make html
En Windows:

Bash

.\make.bat html
```
¡Listo! Sphinx generará todos los archivos HTML en la carpeta build/html. Simplemente abro build/html/index.html en mi navegador para ver el resultado final de mi documentación.
