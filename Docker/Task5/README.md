# Docker Volume and Bind Mount with Nginx

* Create nginx_logs volume to persist Nginx logs and verify it in the default volumes path.
```bash
docker volume create nginx_logs
```
* Create a directory nginx-bind/html to serve a custom HTML file from your host machine.
```bash
mkdir -p nginx-bind/html
```
* Create index.html file with “Hello from Bind Mount” syntax in nginx-bind/html directory.
```bash
echo "Hello from Bind Mount" > nginx-bind/html/index.html
```

* Run Nginx container with the following:
	- Volume for /var/log/nginx
		 
	- Bind Mount for /usr/share/nginx/html 
	```bash 
	docker run -d -p 8080:80 \
	-v nginx_logs:/var/log/nginx \
	-v $(pwd)/nginx-bind/html/:/usr/share/nginx/html nginx
	```


* Verify Nginx page by running curl command from your local machine.
```bash 
curl localhost:8080
```

* Change in the index.html file in your local machine then verify Nginx page again.
```bash 
echo "Hello from Ivlove" > nginx-bind/html/index.html
```
* Verify logs is stored in the nginx_logs volume.
```bash
# Use docker volume inspect to get the volume path
docker volume inspect nginx_logs
sudo ls Volume_path
```

* Delete the volume.
```bash 
docker stop nginx-container
docker rm nginx-container
docker volume rm nginx_logs
```
