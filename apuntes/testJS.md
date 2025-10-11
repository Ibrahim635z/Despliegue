# Guía para Realizar Pruebas en JavaScript con Jest

Esta es mi guía de pasos para configurar y ejecutar pruebas unitarias en un proyecto de Node.js usando el framework Jest.

---

## 1. Configurar el Proyecto

Primero, me aseguro de tener un proyecto de Node.js. Si estoy empezando desde cero, abro la terminal en la carpeta del proyecto y ejecuto:

```bash
npm init -y
```

Esto creará un archivo package.json que gestiona las dependencias y scripts de mi proyecto.

---

## 2. Instalar Jest
A continuación, instalo Jest como una dependencia de desarrollo, ya que solo la necesito para probar mi código, no para la ejecución final de la aplicación.
```
Bash

npm install --save-dev jest
```

---

## 3. Modificar el Código para que sea Exportable
Jest necesita que mi código esté en un módulo para poder "importarlo" y probarlo. Para que mis funciones sean accesibles desde otros archivos, tengo que exportarlas.

Modifico mi archivo de JavaScript (por ejemplo, conversor.js) para que se vea así:
```
JavaScript

/**
 * Convierte una temperatura de grados Celsius a Fahrenheit.
 *
 * @param {number} celsius La temperatura en grados Celsius.
 * @returns {number} La temperatura equivalente en grados Fahrenheit.
 */
function celsiusToFahrenheit(celsius) {
  return (celsius * 9/5) + 32;
}
// Exporta la función para que Jest pueda usarla
module.exports = celsiusToFahrenheit;
```

---

## 4. Crear el Archivo de Prueba
Ahora, creo un nuevo archivo para mis tests. Por convención, lo nombro con el formato **nombreDelArchivo.test.js.** Para este ejemplo, lo llamaré conversor.test.js.

Dentro de este archivo, escribo mis pruebas usando la sintaxis de Jest:
```
JavaScript

// Importo la función que quiero probar
const celsiusToFahrenheit = require('./conversor.js');

// `describe` agrupa un conjunto de pruebas relacionadas
describe('celsiusToFahrenheit', () => {

  // Primer caso de prueba: un valor positivo
  test('should convert 0°C to 32°F', () => {
    // `expect` declara mi "expectativa" y `toBe` es el "matcher" que comprueba el resultado
    expect(celsiusToFahrenheit(0)).toBe(32);
  });

  // Segundo caso de prueba: un valor negativo
  test('should convert -40°C to -40°F', () => {
    expect(celsiusToFahrenheit(-40)).toBe(-40);
  });

  // Tercer caso de prueba: un valor decimal que da un entero
  test('should convert 25°C to 77°F', () => {
    expect(celsiusToFahrenheit(25)).toBe(77);
  });
  
  // Opcional: prueba de que maneja valores no numéricos
  test('should return NaN for non-numeric input', () => {
    expect(celsiusToFahrenheit('abc')).toBe(NaN);
    expect(celsiusToFahrenheit(null)).toBe(32); // (null * 9/5) + 32 = 0 + 32 = 32
  });
});
```

---

## 5. Configurar package.json y Ejecutar las Pruebas
Para que Jest se ejecute fácilmente, agrego un script a mi archivo package.json. Abro el archivo y busco la sección "scripts". Reemplazo la línea "test" con lo siguiente:
```
JSON

"scripts": {
  "test": "jest"
},
```
Finalmente, para correr mis pruebas, voy a la terminal y ejecuto:
```
Bash

npm test
```
Jest buscará automáticamente todos los archivos .test.js en el proyecto y ejecutará las pruebas que contengan.