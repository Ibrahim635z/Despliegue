# Despliegue Automatizado de Servidor Web (Prod vs Dev)

Este proyecto implementa un flujo de trabajo CI/CD para el despliegue de una aplicación web estática utilizando Nginx y Docker. Se han diseñado dos estrategias diferenciadas según el entorno.

## Tecnologías
- **Docker**: Containerización.
- **Nginx**: Servidor Web.
- **GitHub Actions**: Automatización.

## Estrategias de Despliegue

### 1. Entorno de Producción (Rama `main`)
**Objetivo:** Estabilidad e Inmutabilidad.
En este entorno, utilizamos un enfoque tradicional de Docker.
- **Workflow:** `deploy-prod.yml`
- **Funcionamiento:** Se construye una imagen Docker (`docker build`) que contiene el código fuente y la configuración "quemada" dentro.
- **Ventaja:** Garantiza que la versión desplegada no cambie accidentalmente. Si el servidor se reinicia, la imagen sigue teniendo la configuración original.

### 2. Entorno de Desarrollo (Rama `develop`)
**Objetivo:** Iteración rápida y Configuración Dinámica.
Aquí es donde hemos realizado el cambio solicitado para permitir cambios frecuentes en la configuración del servidor web.
- **Workflow:** `deploy-dev.yml`
- **Funcionamiento:** Utilizamos **Docker Volumes**. No construimos una imagen nueva cada vez.
    1. GitHub Actions copia los archivos `.conf` y `.html` al servidor usando SCP.
    2. El contenedor tiene montado el archivo de configuración:
       `-v ./nginx/default.conf:/etc/nginx/conf.d/default.conf`
    3. Se ejecuta `nginx -s reload` para aplicar cambios instantáneamente sin detener el contenedor.

## Instrucciones de Instalación
1. Clonar el repositorio.
2. Configurar los secretos en GitHub (`SERVER_HOST`, `SSH_PRIVATE_KEY`, etc).
3. Hacer push a la rama `main` para desplegar en puerto 8080 (Prod).
4. Hacer push a la rama `develop` para desplegar en puerto 8081 (Dev).

## Capturas
*(Aquí insertarías tus capturas de pantalla de GitHub Actions ejecutándose y del navegador mostrando la web)*