# Guía para Configurar VSCode para Testing

Configurar mi entorno de Visual Studio Code y empezar a escribir y ejecutar pruebas para diferentes lenguajes.

---

## 1. Configurar VSCode para Testing

El primer paso es instalar las extensiones que me darán la mejor experiencia al trabajar con pruebas. Abro VSCode, voy a la pestaña de **Extensiones** (`Ctrl+Shift+X`) y busco e instalo las siguientes:

* **Python**: `Python` (de Microsoft). Esta extensión viene con soporte integrado para frameworks como `pytest` y `unittest`.
* **PHP**: `PHP Intelephense` (de Ben Mewburn) y `PHPUnit Test Explorer` (de Sebastian Kahl). Esta última me permite ver y ejecutar pruebas desde una interfaz gráfica.
* **JavaScript**: `Jest Runner` (de Conner Taylor). Si uso Jest, esta es la mejor opción para ejecutar pruebas directamente desde el editor.

---

## 2. Testing en Python con Pytest

`Pytest` es el framework de testing más popular en Python por su sencillez y potencia.

### 2.1. Instalación y Configuración

1.  **Instalar Pytest**: Abro la terminal de VSCode (`Terminal` > `New Terminal`) en la raíz de mi proyecto e instalo `pytest`.

    ```bash
    pip install pytest
    ```
    > **Nota:** La integración con VSCode ya viene incluida en la extensión principal de Python, por lo que no se necesita ningún paquete adicional como `pytest-vscode-docker`.

2.  **Configurar el Descubrimiento de Pruebas en VSCode**:
    * Abro la paleta de comandos de VSCode (`Ctrl+Shift+P`).
    * Escribo y selecciono **"Python: Configure Tests"**.
    * Elijo **`pytest`** como mi framework de testing.
    * Selecciono el directorio que contiene las pruebas (normalmente, la raíz del proyecto).
    * VSCode configurará automáticamente los archivos necesarios para detectar mis pruebas.

### 2.2. Escribir las Pruebas

Creo un archivo de prueba. Los archivos para Pytest deben empezar con `test_` o terminar con `_test.py`. Las funciones de prueba también deben empezar con `test_`.

**Ejemplo (`test_calculadora.py`):**
```python
# No es necesario importar pytest si solo usas `assert`
# Esta es una función normal de mi aplicación
def sumar(a, b):
    return a + b

# Esta es la función de prueba que verifica el comportamiento de sumar()
def test_sumar():
    assert sumar(2, 3) == 5
    assert sumar(-1, 1) == 0
    assert sumar(0, 0) == 0

 ```

 `assert` es una palabra clave de Python que Pytest utiliza para verificar si una condición es verdadera. Si es falsa, la prueba falla.

### 2.3. Ejecutar las Pruebas
Tengo dos maneras principales de ejecutar las pruebas que he escrito.

Desde la Terminal
Simplemente ejecuto el siguiente comando:
```
Bash

pytest
```

Desde la Interfaz de VSCode
La extensión de Python detectará automáticamente mis pruebas. Puedo ir al panel de Testing en la barra lateral (el icono del matraz o erlenmeyer) para ver, ejecutar y depurar mis pruebas individualmente o en grupo con los botones de "play" y "debug".