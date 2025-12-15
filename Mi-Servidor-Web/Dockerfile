# Uso la imagen oficial ligera de Nginx
FROM nginx:alpine

# Copio mi configuracion de nginx y la coloco en el default del servidor
COPY nginx/default.conf /etc/nginx/conf.d/default.conf

# copio mi frontend en el servidor
COPY html /usr/share/nginx/html

# Expongo el puerto 80
EXPOSE 80