# Этап сборки
FROM maven:3.9.4-eclipse-temurin-17 AS builder
WORKDIR /app
COPY ./pom.xml .
COPY src ./src
RUN mvn clean package -DskipTests

# Этап выполнения
FROM eclipse-temurin:17-jre
WORKDIR /app
COPY --from=builder /app/target/*.jar /app/app.jar

ENTRYPOINT ["java", "-jar", "/app/app.jar"]
