# Stage 0, "build-stage", based on Node.js, to build and compile the frontend
FROM node:10 as build-stage

WORKDIR /usr/app

COPY package*.json /usr/app/

RUN npm install

COPY ./ /usr/app/

RUN npm run build

# Stage 1, based on Nginx, production-ready
FROM zalari/nginx-html5
COPY --from=build-stage /usr/app/build/ /usr/share/nginx/html