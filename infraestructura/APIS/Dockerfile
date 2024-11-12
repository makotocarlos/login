FROM node:20

USER root

RUN apt-get update && apt-get install -y wget nano postgresql postgresql-contrib && rm -rf /var/lib/apt/lists/*

RUN npm cache clean --force

RUN npm install -g npm@8.12.1

RUN npm install -g prisma \
    && npm install -g cors \
    && npm install -g pg \
    && npm install -g dotenv \
    && npm install -g express \
    && npm install -g jsonwebtoken \
    && npm install -g nodemon \
    && npm install -g @prisma/client

RUN mkdir -p /usr/userAPI

WORKDIR /usr/userAPI

COPY login/package*.json ./

RUN npm install

COPY login ./

RUN npx prisma generate

CMD ["npx", "nodemon", "app.js"]
