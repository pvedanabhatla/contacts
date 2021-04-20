FROM node:alpine as builder
WORKDIR '/app'
COPY ./package.json ./
RUN apk add --update nodejs npm
RUN apk add --update npm
RUN npm install 
RUN npm install -g @angular/cli@8.3.18
COPY . .
RUN echo "################"
RUN pwd
RUN ls -alrt
RUN echo "@@@@@@@@@@@@@@@@"
RUN npm run build

FROM nginx
EXPOSE 4200
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
COPY --from=builder /app/dist /usr/share/nginx/html