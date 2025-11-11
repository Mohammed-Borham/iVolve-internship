Lab 11: Managing Docker Environment Variables Across Build and Runtime 
1. Clone the Application Code https://github.com/Ibrahim-Adel15/Docker-3.git
	$ git clone <url> 
2. Write Dockerfile

	* Use python image 
		- FROM python:3.10-slim
	* Install flask
		- RUN pip install flask * Expose port 8080
		- EXPOSE 8080
	* Run python command on app.py 
		- CMD ["python", "app.py"]
	* Build Docker Image
		- docker build -t <image-name> .

3. Run container and set both environment variables (APP_MODE & APP_REGION) as following: 
	* (development, us-east) as variables in the command when run docker container
		- docker run -d -p 8080:8080 -e APP_MODE=development -e APP_REGION=us-east <image-name> 
	
	* (staging, us-west) in a separate file and  pass the file name in the command
		- create env-file & add variables on it 
		- docker run -d -p 8080:8080 --env-file env-file <image-name>
	
	* (production, canada-west) in the Dockerfile
		- update Dockerfile 
			* ENV APP_MODE=production
			* ENV APP_REGION=canada-west
		- build docker image
		- run container

