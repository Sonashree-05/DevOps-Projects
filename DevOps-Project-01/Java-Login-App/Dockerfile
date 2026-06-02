FROM maven:3.9.16-eclipse-temurin-17 AS builder

WORKDIR /app

COPY . .

RUN mvn clean package -DskipTests

FROM eclipse-temurin:11-jre 

WORKDIR /app

COPY --from=builder /app/target/*.war app.war

EXPOSE 8080

ENTRYPOINT ["java","-jar","app.war"]
