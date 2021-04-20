FROM node:alpine as builder
WORKDIR '/app'
COPY ./package.json ./
RUN apk add --update nodejs npm
RUN apk add --update npm
RUN npm install
COPY . .
RUN echo "################"
RUN pwd
RUN ls -alrt
RUN echo "@@@@@@@@@@@@@@@@"
RUN ls -lrt $HOME
RUN npm run build

FROM nginx
EXPOSE 4200
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
COPY --from=builder /app/dist /usr/share/nginx/html