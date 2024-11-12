## If you would like to use docker and Kubernetes sandbox environment , you can use below:
```
https://labs.play-with-docker.com/
https://labs.play-with-k8s.com/
```
## Download Docker desktop client
```
https://www.docker.com/products/docker-desktop/
```
## Get started
  - Clone a sample git repository using the below command or use your project for the demo:
```
git clone https://github.com/docker/getting-started-app.git
```
  - cd into the directory
cd getting-started-app/
  - Create an empty file with the name Dockerfile
touch Dockerfile
  - Using the text editor of your choice, paste the below content ( Details about each of these have already shared in the video)
```
FROM openjdk:17-jdk-slim
WORKDIR /app
COPY target/myapp-0.0.1-SNAPSHOT.jar app.jar
EXPOSE 8080
ENTRYPOINT ["java", "-jar", "app.jar"]
```
  - Package your Spring Boot application using Maven or Gradle.
```
./mvnw clean package  # for Maven
./gradlew build       # for Gradle
```
  - Build the docker image using the application code and Dockerfile
```
docker build -t todo_app .
```
  - Verify the image has been created and stored locally using the below command:
```
docker images
```
  - Create a public repository on hub.docker.com and push the image to remote repo
```
docker login
docker tag todo_app:latest username/new-reponame:tagname
docker images
docker push username/new-reponame:tagname
```
  - To pull the image to another environment , you can use below command
```
docker pull username/new-reponame:tagname
```
  - To start the docker container, use below command
```
docker run -dp 8080:8080 username/new-reponame:tagname
```
  - Verify your app. If you have followed the above steps correctly, your app should be listening on localhost:8080
  - To enter(exec) into the container, use the below command
```
docker exec -it containername sh
or
docker exec -it containerid sh
```
  - To view docker logs
```
docker logs containername
or
docker logs containerid
```
