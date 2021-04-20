FROM node:alpine as builder
WORKDIR '/app'
COPY ./package.json ./
RUN apk update && apk install -y curl
RUN curl -sL https://deb.nodesource.com/setup_8.x | bash -
RUN apk update && apk install -y nodejs
RUN npm install
COPY . .
RUN npm run build

FROM nginx
EXPOSE 4200
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
COPY --from=builder /app/dist /usr/share/nginx/html