Lab 10: Multi-Stage Build for a Node.js App
1. Clone the Application Code https://github.com/Ibrahim-Adel15/Docker-1.git
	$ git clone <url>


2. Write Dockerfile with Multi-stage.

	*Use Maven base image for first stag
		$ FROM maven:3.8.5-openjdk-17-slim AS builder 
	*Copy the application code into the container
		$ WORKDIR /app
		$ COPY . . 
	*Build the app using mvn package
		$ RUN mvn clean package 
	*Use java base image for second stag
		$ FROM eclipse-temurin:17-jre-jammy 
	*Copy JAR file from first stag
		$ WORKDIR /app
		$ COPY  --from=builder  /app/target/*.jar app.jar
 
	*Expose port 8080 & Run the app
		$ EXPOSE 8080
		$ CMD ["java","-jar","app.jar"]

3. Build App3 Image (Note the image size).
	$ docker build -t task3-img .
4. Run the container.
	$ docker run -d -p 9595:8080 --name app3 task3-img
5 .Test the Application.
	$ curl localhost:9595


