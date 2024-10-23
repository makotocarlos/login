FROM node:20

USER root

RUN apt-get update && apt-get install -y \
    wget \
    nano

# Limpia la caché de npm
RUN npm cache clean --force

# Actualiza npm a una versión específica
RUN npm install -g npm@8.12.1

# Instala las dependencias globales necesarias
RUN npm install -g prisma \
    && npm install -g cors \
    && npm install -g dotenv \
    && npm install -g express \
    && npm install -g jsonwebtoken \
    && npm install -g nodemon \
    && npm install -g @prisma/client

# Crea el directorio de la aplicación
RUN mkdir -p /usr/userAPI

# Establece el directorio de trabajo
WORKDIR /usr/userAPI

# Copia el archivo package.json y package-lock.json
COPY login/package*.json ./

# Instala las dependencias del proyecto
RUN npm install

# Copia el resto de la aplicación
COPY login ./

# Genera los archivos de Prisma
RUN npx prisma generate

# Cambia el comando para usar nodemon
CMD ["npx", "nodemon", "app.js"]
