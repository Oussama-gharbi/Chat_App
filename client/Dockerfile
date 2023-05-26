FROM node:14-alpine AS build
WORKDIR /client
RUN ls
COPY ./package*.json ./
RUN npm i -g npm@latest
COPY . .
RUN npm run build

RUN ls
# ## Replace the default nginx index page with our react  app
FROM  nginx:1.21.0-alpine
COPY --from=build ./client/build /usr/share/nginx/html
RUN ls /usr/share/nginx/html
COPY ./nginx.conf /etc/nginx/sites-avaialbe/default.conf  
EXPOSE 80
# Launch app with PM2

ENTRYPOINT ["nginx", "-g", "daemon off;"]
