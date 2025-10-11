<h1>Guía Rápida de Comandos: Documentación (JSDoc) y Testing (Jest)</h1>

---


<h3>Parte 1: Documentación con JSDoc</h3>

**1. Inicializar el Proyecto**

`Comando: npm init -y`

Qué hace: Crea el archivo package.json para gestionar el proyecto.

**2. Instalar JSDoc**

`Comando: npm install --save-dev jsdoc`

Qué hace: Instala JSDoc como una dependencia de desarrollo en tu proyecto.

**3. Crear Archivo de Configuración (jsdoc.json)**

Qué hacer: Crea un archivo llamado jsdoc.json en la raíz del proyecto.

Contenido:
```
JSON

{
    "source": {
        "include": ["."],
        "includePattern": ".+\\.js(doc|x)?$",
        "exclude": ["node_modules"]
    },
    "opts": {
        "encoding": "utf8",
        "destination": "./docs/",
        "recurse": true
    }
}
```

**4. Añadir Script a package.json**

Qué hacer: Dentro de package.json, añade el script docs.

Contenido:
```
JSON

"scripts": {
  "docs": "jsdoc -c jsdoc.json"
}
```
**5. Documentar el Código**

Qué hacer: Usa el formato de bloque /** ... */ encima de las funciones.

Ejemplo:
```
JavaScript

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
**6. Generar la Documentación**

`Comando: npm run docs`

Qué hace: Ejecuta JSDoc, lee tu código y crea la carpeta docs/ con la documentación en HTML. Para verla, abre docs/index.html.

---

<h3>Parte 2: Pruebas Unitarias con Jest</h3>

**1. Instalar Jest**

`Comando: npm install --save-dev jest`

Qué hace: Instala Jest como una dependencia de desarrollo.

**2. Añadir Script de Test a package.json**

Qué hacer: Añade el script test a tu package.json. Si ya tenías el de docs, simplemente añade una coma.

Contenido:
```
JSON

"scripts": {
  "docs": "jsdoc -c jsdoc.json",
  "test": "jest"
}
```

**3. Exportar Código para Pruebas**

Qué hacer: En tu archivo .js, exporta la función que quieres probar.

`Ejemplo: module.exports = sumar;`

**4. Crear Archivo de Test**

Qué hacer: Crea un archivo con el sufijo .test.js (ej: sumar.test.js).

Contenido de ejemplo:
```
JavaScript

const sumar = require('./sumar.js');

test('debe sumar 1 + 2 para que sea igual a 3', () => {
  expect(sumar(1, 2)).toBe(3);
});
```

**5. Ejecutar las Pruebas**

`Comando: npm test`

Qué hace: Lanza Jest, que ejecuta todos los archivos de test y muestra un informe de resultados en la consola.