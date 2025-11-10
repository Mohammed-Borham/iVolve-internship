## Build stage
FROM maven:3.8.5-openjdk-17-slim AS builder
WORKDIR /app
COPY . . 
RUN mvn clean package 

## Run stage
FROM eclipse-temurin:17-jre-jammy
WORKDIR /app
COPY  --from=builder  /app/target/*.jar app.jar
EXPOSE 8080
CMD ["java","-jar","app.jar"]
