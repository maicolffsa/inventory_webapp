# Usa una imagen base para Node.js
FROM node:18 AS build

WORKDIR /app

# Copia los archivos y carpetas necesarios
COPY ./package.json ./package-lock.json ./
RUN npm install

COPY ./ ./
RUN npm run build

# Sirve los archivos estáticos con Nginx
FROM nginx:latest

COPY --from=build /app/dist /usr/share/nginx/html