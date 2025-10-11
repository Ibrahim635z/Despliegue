# Guía para Documentar Proyectos JavaScript con JSDoc

Esta es mi guía personal para documentar mi código JavaScript usando JSDoc y `npm`.


---

## 1. Configuración del Proyecto

Para empezar, necesito inicializar mi proyecto de Node.js e instalar JSDoc como dependencia de desarrollo.

### 1.1. Inicializar el Proyecto

Ejecuto este comando en la terminal, en la raíz de mi proyecto. La bandera `-y` acepta todas las opciones por defecto.

```bash
npm init -y
```
Esto creará un archivo package.json en la raíz del proyecto.

### 1.2. Instalar JSDoc
Instalo la dependencia jsdoc solo para este proyecto, como una herramienta de desarrollo.
```
Bash

npm install --save-dev jsdoc
```
Esto creará una carpeta node_modules (si no existe) y un archivo package-lock.json.

---

## 2. Documentar el Código JavaScript
Para comentar mi código, uso el mismo formato de bloques de comentario que en PHP, empezando con /** y terminando con */ justo encima de una función, clase o variable.

JavaScript
```

/**
 * Suma dos números y devuelve el resultado.
 * @param {number} a - El primer número.
 * @param {number} b - El segundo número.
 * @returns {number} La suma de a y b.
 */
function sumar(a, b) {
  return a + b;
}

```
## 3. Generar la Documentación HTML
Para facilitar la generación de la documentación, configuro un script de npm y un archivo de configuración para JSDoc.

### 3.1. Añadir el Script a package.json
Abro mi archivo package.json y añado un script llamado "docs" dentro del objeto scripts.
```
JSON

"scripts": {
  "docs": "jsdoc -c jsdoc.json"
}
```
### 3.2. Crear el Archivo de Configuración jsdoc.json
Creo un archivo nuevo llamado jsdoc.json en la raíz de mi proyecto. Este archivo le dice a JSDoc qué carpetas escanear y dónde guardar el resultado.

```
JSON

{
    "source": {
        "include": ["."],
        "exclude": ["node_modules"],
        "includePattern": ".+\\.js(doc|x)?$"
    },
    "opts": {
        "encoding": "utf8",
        "destination": "./docs/",
        "recurse": true
    }
}
```
Explicación: Esta configuración escanea todos los archivos .js en el proyecto (.) de forma recursiva, excluyendo node_modules, y guarda la documentación HTML en la carpeta ./docs/.

### 3.3. Ejecutar el Comando de Generación
Ahora, para generar la documentación, simplemente ejecuto el siguiente comando en la terminal:
```
Bash

npm run docs
```
Este comando ejecutará JSDoc con la configuración que definí, leerá mi código y generará la carpeta docs con todos los archivos HTML.

---

### 4. Ver la Documentación Generada
Una vez que el comando npm run docs termine, veré una nueva carpeta llamada docs en mi proyecto.

Para ver la documentación, solo tengo que abrir el archivo index.html que se encuentra dentro de la carpeta docs con mi navegador web.

