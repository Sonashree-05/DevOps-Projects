FROM maven:3.9.16-eclipse-temurin-17 AS builder

WORKDIR /app

COPY . .

RUN mvn clean package -DskipTests

FROM gcr.io/distroless/java11-debian11 

WORKDIR /app

COPY --from=builder /app/target/*.war app.war

EXPOSE 8080

ENTRYPOINT ["java","-jar","/app/app.war"]
