# Guía para Testing en PHP con PHPUnit

Configurar y ejecutar pruebas unitarias en mis proyectos de PHP, utilizando PHPUnit, el estándar de facto en el ecosistema.

---

## 1. Instalación y Configuración

Primero, necesito añadir PHPUnit a mi proyecto y configurarlo para que sepa dónde encontrar mis pruebas.

### 1.1. Instalar PHPUnit con Composer

Abro la terminal en la raíz de mi proyecto e instalo PHPUnit como una dependencia de desarrollo.

```bash
composer require --dev phpunit/phpunit
```
### 1.2. Crear el Archivo de Configuración
Creo un archivo llamado phpunit.xml en la raíz de mi proyecto. Este archivo le indica a PHPUnit cómo debe ejecutarse.
```
XML

<?xml version="1.0" encoding="UTF-8"?>
<phpunit colors="true">
    <testsuites>
        <testsuite name="Project Tests">
            <directory>tests</directory>
        </testsuite>
    </testsuites>
</phpunit>
```
**Nota**: Esta configuración le dice a PHPUnit que todas las pruebas se encontrarán dentro de una carpeta llamada tests.

---

## 2. Escribir las Pruebas
Ahora procedo a escribir el código de las pruebas.

Crear la carpeta de pruebas: En la raíz de mi proyecto, creo una nueva carpeta llamada tests.

Crear una clase de prueba: Dentro de la carpeta tests, creo un nuevo archivo. Por convención, el nombre del archivo debe terminar en **Test.php.** Por ejemplo, **CalculadoraTest.php.**
```
PHP

<?php declare(strict_types=1);

// Importa la clase base de PHPUnit para tests
use PHPUnit\Framework\TestCase;

// La clase de prueba debe extender TestCase
class CalculadoraTest extends TestCase
{
    // Cada método de prueba debe empezar con la palabra "test"
    public function testSumar(): void
    {
        // Asumo que tengo una clase Calculadora en mi proyecto
        // y que está siendo autocargada por Composer.
        $calc = new \Calculadora();

        // Uso aserciones para verificar el resultado
        // assertEquals(valor_esperado, valor_real)
        $this->assertEquals(5, $calc->sumar(2, 3));
        $this->assertEquals(0, $calc->sumar(-1, 1));
    }
}
```

---

## 3. Ejecutar las Pruebas
Tengo dos maneras principales de ejecutar las pruebas que he creado.

### 3.1. Desde la Terminal
La forma más directa es ejecutar el siguiente comando en la terminal desde la raíz del proyecto:
```
Bash

./vendor/bin/phpunit
```
### 3.2. Desde VSCode (con Extensión)
Si tengo instalada la extensión PHPUnit Test Explorer, el proceso es más visual:

Abro el panel de Testing en la barra lateral de VSCode (el icono del matraz o erlenmeyer).

La extensión detectará automáticamente todas mis pruebas.

Puedo ejecutar todas las pruebas, un archivo de pruebas completo o un método de prueba individual haciendo clic en el botón de "play" que aparece al lado de cada uno.
