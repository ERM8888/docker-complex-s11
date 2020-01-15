# Se crea la imagen para construir la aplicacion
FROM node:alpine as builder
WORKDIR '/app'
COPY ./package.json ./
RUN npm install
COPY . .
RUN npm run build
# Se crea la imagen de nginx con los ficheros build de la imagen anterior
FROM nginx
# Se expone el puerto 3000
EXPOSE 3000
# Se copia el fichero de configuracion
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
# Se copia los ficheros del build de la anterior imagen en esta
COPY --from=builder /app/build /usr/share/nginx/html