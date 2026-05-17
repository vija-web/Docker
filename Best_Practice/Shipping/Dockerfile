FROM maven:3.9.11 AS builder
WORKDIR /opt/server
COPY src/ ./src
COPY pom.xml .
RUN mvn clean package
RUN mv target/shipping-1.0.jar shipping.jar 

# --------------------------------------------------

FROM eclipse-temurin:17-jre-alpine
EXPOSE 8080
LABEL project="Roboshop" \
      component="Shipping" \
      created_by="vijay" \
      contact="vijayanthony28667@gmail.com"
WORKDIR /opt/server
RUN addgroup -S roboshop && \
    adduser -S roboshop -G roboshop
ENV CART_ENDPOINT="cart:8080" \
    DB_HOST="mysql"
COPY --from=builder /opt/server/shipping.jar /opt/server/shipping.jar
RUN chown -R roboshop:roboshop /opt/server
USER roboshop
ENTRYPOINT ["java" , "-jar" , "shipping.jar"]