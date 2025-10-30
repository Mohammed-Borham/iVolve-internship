Lab 8: Run Java Spring Boot App in a Container


1.Clone the Application Code https://github.com/Ibrahim-Adel15/Docker-1.git
	$git clone <url>

2. Write Dockerfile.
	# Use Maven base image with java 17
	FROM maven:3.8.5-openjdk-17-slim
	# Create work directory
	WORKDIR /app
	# Copy the application source code into the container
	COPY . . 
	# Build the app using mvn package
	RUN mvn install
	# Run the app on jar file located in target/demo-0.0.1-SNAPSHOT.jar
	CMD ["java","-jar","target/demo-0.0.1-SNAPSHOT.jar"]
	# Expose port 8080
	EXPOSE 8080


3. Build App1 Image (Note the build time & image size) .
	$ docker build -t task1-image .
	# It takes 2 min to build the image & image size is 509MB

4. Run Container.
	$docker run -d -p 8081:8080 --name task1 task1-image

5. Test the Application.
	# there are two ways
	$ curl localhost:8081
	From your browser <http://your_machine_ip:8081>
