FROM node:14-alpine AS build
WORKDIR /client
COPY ./client/package*.json .
RUN npm install
COPY . .
RUN npm run build
# ## Replace the default nginx index page with our react  app
FROM  nginx:1.21.0-alpine
COPY --from=build . /usr/share/nginx/html
COPY ./app/nginx.conf /etc/nginx/sites-avaialbe/default.conf  
EXPOSE 80
# Launch app with PM2

ENTRYPOINT ["nginx", "-g", "daemon off;"]
