Lab 9: Run Java Spring Boot App in a Container

1. Clone the Application Code https://github.com/Ibrahim-Adel15/Docker-1.git

	$git clone <url>

2. Build the JAR file
	$ mvn install

3. Write Dockerfile.
	# Use Java 17 base image
	FROM openjdk:17-slim
	# Create work directory
	WORKDIR /app
	# Copy the JAR file into the container
	COPY target/demo-0.0.1-SNAPSHOT.jar  . 
	# Run the app on jar file  {demo-0.0.1-SNAPSHOT.jar}
	CMD ["java","-jar","demo-0.0.1-SNAPSHOT.jar"]
	# Expose port 8080
	EXPOSE 8080


3. Build App2 Image (Note the build time & image size) .
	$ docker build -t task2-image .
	# It takes less than 4 sec to build the image & image size is 427MB

4. Run Container.
	$docker run -d -p 8082:8080 --name task2 task2-image

5. Test the Application.
	# there are two ways
	   $ curl localhost:8082
	#From your browser 
	   <http://your_machine_ip:8082>
