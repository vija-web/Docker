# BUILD STAGE
FROM python:3.9-alpine3.21 AS build
WORKDIR /opt/server
COPY payment.ini .
COPY *.py .
COPY requirements.txt .
RUN apk add --no-cache \
    gcc \
    musl-dev \
    linux-headers \
    python3-dev \
    build-base \
    pcre-dev
RUN pip3 install --prefix=/install -r requirements.txt

# ------------------------------------------------------

FROM python:3.9-alpine3.21
EXPOSE 8080
LABEL project="Roboshop" \
      component="Payment" \
      created_by="vijay" \
      contact="vijayanthony28667@gmail.com"
WORKDIR /opt/server
RUN apk add --no-cache pcre && \
    addgroup -S roboshop && \
    adduser -S roboshop -G roboshop
ENV CART_HOST="cart" \
    CART_PORT="8080" \
    USER_HOST="user" \
    USER_PORT="8080" \
    AMQP_HOST="rabbitmq" \
    AMQP_USER="roboshop" \
    AMQP_PASS="roboshop123"
COPY --from=build /opt/server /opt/server
COPY --from=build /install /usr/local
RUN chown -R roboshop:roboshop /opt/server && \
    chmod +x /usr/local/bin/uwsgi
USER roboshop
ENTRYPOINT ["uwsgi" , "--ini" , "payment.ini"]
