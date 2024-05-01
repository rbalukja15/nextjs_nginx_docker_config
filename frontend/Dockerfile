FROM node:18.17.0 AS builder

# Set working directory
WORKDIR /usr/src/app

RUN npm config set strict-ssl false
RUN npm config set registry http://registry.npmjs.org/

# Copy all files
COPY . .

RUN npm install

# Build app
RUN npm run build

FROM node:18.17.0 AS server

# Set working directory
WORKDIR /usr/src/app

COPY --from=builder /usr/src/app/next.config.mjs ./
COPY --from=builder /usr/src/app/public ./public
COPY --from=builder /usr/src/app/build ./build
COPY --from=builder /usr/src/app/node_modules ./node_modules
COPY --from=builder /usr/src/app/package.json ./package.json


CMD [ "npm", "run", "start" ]