# Guía para Documentar Proyectos PHP con PHPDocumentor

Configurar un entorno de documentación para proyectos PHP usando Composer y VSCode.

---

## 1. Preparación del Entorno

Antes de empezar con el proyecto, necesito tener las herramientas adecuadas.

### 1.1. Instalar Composer

* Asegurarme de que **Composer** está instalado en mi PC.

### 1.2. Extensiones para VSCode

Instalo las siguientes extensiones en Visual Studio Code para que me ayuden a escribir el código y la documentación:

* **PHP Intelephense:** Proporciona autocompletado avanzado, definiciones, referencias, etc., para PHP.
* **PHP DocBlocker:** Esta extensión es fundamental. Me ayuda a generar bloques de documentación (PHPDoc) automáticamente para mis funciones, clases y métodos.

---

## 2. Cómo Documentar el Código

Para usar `PHP DocBlocker` y generar un bloque de documentación:

1.  Coloco el cursor justo encima de la línea de código que quiero documentar (por ejemplo, `class MiClase {`).
2.  Escribo `/**` y presiono `Enter`.
3.  La extensión creará automáticamente la plantilla del bloque de comentarios para que la rellene.

---

## 3. Configuración en Mi Proyecto

Para cada proyecto que quiera documentar, sigo estos pasos en la terminal.

### 3.1. Inicializar Composer

Si el proyecto no tiene un archivo `composer.json`, lo inicializo.

```bash
composer init
```

### 3.2. Instalar PHPDocumentor
Añado phpdocumentor como una dependencia de desarrollo. Esto hace que solo se instale en este proyecto y no de forma global.
```
Bash

composer require --dev "phpdocumentor/phpdocumentor:^3.0"
```
---

## 4. Generar los Archivos de Documentación
Una vez que he comentado mi código usando el formato PHPDoc, ejecuto el siguiente comando desde la raíz de mi proyecto para generar la documentación en formato HTML.
```
Bash

./vendor/bin/phpdoc -d . -t docs
-d . le dice a PHPDocumentor que analice el directorio actual.

-t docs le indica que guarde los archivos HTML generados en una carpeta llamada docs.
```
¡Y listo! Con esto, se creará la carpeta docs con toda la documentación navegable de mi código.