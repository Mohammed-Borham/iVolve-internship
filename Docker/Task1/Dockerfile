FROM maven:3.8.5-openjdk-17-slim
WORKDIR /app
COPY . . 
RUN mvn install
CMD ["java","-jar","target/demo-0.0.1-SNAPSHOT.jar"]
EXPOSE 8080
