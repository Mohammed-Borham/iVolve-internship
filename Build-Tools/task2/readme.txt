Lab 7: Building and Packaging Java Applications with maven


1- Install maven.
	$ sudo apt install maven
	# Using mavne docs https://maven.apache.org/install.html

2- Clone source code https://github.com/Ibrahim-Adel15/build2.git
	$ git clone <url>

3- Run Unit test.
	$ mvn test

4- Build App [ generate artifact in target/ hello-ivolve-1.0-SNAPSHOT.jar ].
	$ mvn install

5- Run App.
	$ java -jar /target/<app_name>.jar

