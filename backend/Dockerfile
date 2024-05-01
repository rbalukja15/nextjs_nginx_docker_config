FROM node:18-alpine AS base

WORKDIR /usr/src/app

COPY ./package.json /usr/src/app/package.json
COPY ./package-lock.json /usr/src/app/package-lock.json
RUN npm ci

COPY . .

CMD ["node", "server.js"]