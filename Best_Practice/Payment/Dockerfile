# BUILD STAGE
FROM python:3.9-alpine3.21 AS build
WORKDIR /opt/server
COPY payment.ini .
COPY *.py .
COPY requirements.txt .
RUN pip3 install -r requirements.txt

# ------------------------------------------------------

FROM python:3.9-alpine3.21
EXPOSE 8080
LABEL project="Roboshop" \
      component="Payment" \
      created_by="vijay" \
      contact="vijayanthony28667@gmail.com"
WORKDIR /opt/server
RUN addgroup -S roboshop && \
    adduser -S roboshop -G roboshop
ENV CART_HOST="cart" \
    CART_PORT="8080" \
    USER_HOST="user" \
    USER_PORT="8080" \
    AMQP_HOST="rabbitmq" \
    AMQP_USER="roboshop" \
    AMQP_PASS="roboshop123"
COPY --from=build /opt/server /opt/server
RUN chown -R roboshop:roboshop /opt/server
USER roboshop
ENTRYPOINT ["uwsgi" , "--ini" , "payment.ini"]
