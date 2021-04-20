FROM node:alpine as builder
WORKDIR '/app'
COPY ./package.json ./
RUN npm clean cache
RUN npm install
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