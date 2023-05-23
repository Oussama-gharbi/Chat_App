FROM node:18-alpine
RUN mkdir -p /server
WORKDIR /server
#COPY ./app/package*.json ./
COPY server .
RUN npm  install 
EXPOSE 5000
#CMD ["/usr/sbin/nginx", "-g", "daemon off;"]
ENTRYPOINT ["node", "index.js"]
