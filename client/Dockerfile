# Specify a base image
FROM node:alpine as builder

WORKDIR /usr/app/

# Install some depenendencies
COPY ./package.json ./
RUN npm install
COPY ./ ./
RUN npm run build

# From 0 recupera lo generado en la anterior generacion
FROM nginx
EXPOSE 3000
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
COPY --from=builder /usr/app/build /usr/share/nginx/html