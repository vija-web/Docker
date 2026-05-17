# BUILD Stage
FROM node:20.19.5-alpine3.21 AS build
WORKDIR /opt/server
COPY package.json .
COPY *.js .
RUN npm install

# ---------------------------------------------

FROM node:20.19.5-alpine3.21
EXPOSE 8080
LABEL project="Roboshop" \
      created_by="vijay" \
      component="Cart" \
      contact="vijayanthony28667@gmail.com"
WORKDIR /opt/server
RUN addgroup -S roboshop && \
    adduser -S roboshop -G roboshop
ENV REDIS_HOST="redis" \
    CATALOGUE_HOST="catalogue" \
    CATALOGUE_PORT="8080"
COPY --from=build /opt/server /opt/server
RUN chown -R roboshop:roboshop /opt/server
USER roboshop
ENTRYPOINT ["node" , "server.js"]