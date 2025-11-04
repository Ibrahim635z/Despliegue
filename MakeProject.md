# Crear un proyecto desde  0

---

## Creacion

```
# 1. Crea la carpeta del proyecto y entra en ella
mkdir mi-proyecto-s3
cd mi-proyecto-s3

# 2. Inicializa un proyecto de Node.js
# El flag -y acepta todas las opciones por defecto y crea 'package.json'
npm init -y

# 3. Inicializa un repositorio de Git
git init

# 4. Crea un archivo .gitignore para excluir archivos innecesarios
touch .gitignore

```

## Gitignore 

```
# Dependencias
node_modules/

# Archivos de configuración y logs
.env
*.log

# Documentación generada
docs/
```

## Crear la estructura de la App

```
# 1. Crea una carpeta 'src' para tu código fuente
mkdir src

# 2. Crea los archivos de tu aplicación (tú pondrás el contenido)
touch src/index.html
touch src/style.css
touch src/app.js

# 3. Crea una carpeta para las pruebas
mkdir tests
touch tests/app.test.js
```

**Añades el JS y el HTML**

## Instalar y configurar dependencias (JSDocs y Jest)

```
# Instalar Jest y JSDoc
npm install jest jsdoc --save-dev
```

## Configurar el PackageJson
**Añadir scripts**
```
{
  "name": "mi-proyecto-s3",
  "version": "1.0.0",
  "description": "",
  "main": "src/app.js",
  "scripts": {
    "test": "jest",
    "docs": "jsdoc src/app.js -d docs"
  },
  "keywords": [],
  "author": "",
  "license": "ISC",
  "devDependencies": {
    "jest": "^29.0.0", // La versión puede variar
    "jsdoc": "^4.0.0"  // La versión puede variar
  }
}
```

## Crear Prueba unitaria

**Tests/app.test.js**

Colocamos El js correspondiente por ejemplo:

```
const sumar = require('../src/app.js');

describe('Pruebas para la función sumar', () => {
    test('sumar 1 + 2 debe ser igual a 3', () => {
        expect(sumar(1, 2)).toBe(3);
    });

    test('sumar -5 + 10 debe ser igual a 5', () => {
        expect(sumar(-5, 10)).toBe(5);
    });
});
```

## Comprobacion local

```
# 1. Ejecuta las pruebas unitarias
npm test
# Deberías ver un mensaje de que las pruebas han pasado ("PASS")

# 2. Genera la documentación
npm run docs
# Verás que se crea una nueva carpeta 'docs' con archivos HTML
```

## Subirlo a Github

```
# 1. Crea un nuevo repositorio en GitHub.com (ej: 'mi-proyecto-s3')

# 2. Conecta tu repositorio local con el remoto
git remote add origin https://github.com/TU_USUARIO/mi-proyecto-s3.git

# 3. Crea la rama 'main' (si Git no la creó por defecto)
git branch -M main

# 4. Haz tu primer commit
git add .
git commit -m "feat: configuración inicial del proyecto con Jest y JSDoc"

# 5. Sube tus cambios a GitHub
git push -u origin main
```

## Ramas
```
# 1. Crea la rama 'dev' a partir de 'main'
git checkout -b dev
git push -u origin dev

# 2. Crea tu rama 'feature' a partir de 'dev'
git checkout -b feature/despliegue-s3
git push -u origin feature/despliegue-s3
```