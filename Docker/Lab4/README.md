# Lab 4: Docker Image Optimization and Export/Load

## 1. Cloning the Repository

```bash
git clone https://github.com/Ibrahim-Adel15/ImageOptimization-.git
cd ImageOptimization-
```

## 2. Building the Original Image

```bash
docker build -t image1 .
```

Check the image and its size:

```bash
docker images image1
```

<img width="1628" height="66" alt="image" src="https://github.com/user-attachments/assets/369ec73b-387a-4027-98f7-f9a160c307d1" />


## 3. Running and Testing Container1

```bash
docker run -d --name container1 -p 8080:8080 image1
```

Check the container and application logs:

```bash
docker ps
docker logs container1
```
<img width="1911" height="402" alt="image" src="https://github.com/user-attachments/assets/abb9d3ac-1dd5-4794-845a-f131ba469546" />

Test the application:

```bash
curl -i http://localhost:8080/
```

<img width="869" height="139" alt="image" src="https://github.com/user-attachments/assets/5a138a2e-fa5a-434d-89e4-40197b1a8b0c" />

Stop & delete the container:

```bash
docker stop container1
docker rm container1
```


## 4. Creating the Optimized Dockerfile

Create a new Dockerfile:

```bash
 vim Dockerfile2
```

Add the following code:

```dockerfile
# Build stage
FROM maven:3.9.15-eclipse-temurin-17-alpine AS builder

WORKDIR /app
COPY pom.xml .
COPY src ./src

RUN mvn package

# Runtime stage
FROM eclipse-temurin:17-jre-alpine

WORKDIR /app

RUN addgroup -S appgroup && adduser -S appuser -G appgroup

COPY --from=builder /app/target/demo-0.0.1-SNAPSHOT.jar app.jar

RUN chown appuser:appgroup /app/app.jar

USER appuser

EXPOSE 8080

CMD ["java", "-jar", "app.jar"]
```


## 5. Building and Comparing Images

Build the optimized image:

```bash
docker build -f Dockerfile2 -t image2 .
```

Compare the image sizes:

```bash
docker images image1
docker images image2
```

<img width="792" height="165" alt="image" src="https://github.com/user-attachments/assets/3328dc0d-f1f8-46ce-9de1-d280b5cb36cf" />


## 6. Running and Testing Container2

```bash
docker run -d --name container2 -p 8080:8080 image2
```

Check the application:

```bash
docker logs container2
curl -i http://localhost:8080/
```
<img width="1911" height="405" alt="image" src="https://github.com/user-attachments/assets/d7dd9d32-d890-4aa6-a94b-ebb654233aac" />

<img width="843" height="144" alt="image" src="https://github.com/user-attachments/assets/b82bd75b-2a94-40cd-b3ed-e10fe0493930" />

Verify that the container runs as a non-root user:

```bash
docker exec container2 whoami
```
<img width="845" height="42" alt="image" src="https://github.com/user-attachments/assets/3c424587-3438-416e-badb-e79b332d6f51" />


## 7. Stopping and Removing Container2

```bash
docker stop container2
docker rm container2
```


## 8. Saving the Image as a TAR File

```bash
docker save -o lab-image.tar image2
```

Verify the archive:

```bash
ls -lh
```

<img width="657" height="154" alt="image" src="https://github.com/user-attachments/assets/f1827c16-1592-4604-acf1-344d2363484a" />


## 9. Removing the Optimized Image

```bash
docker rmi image2
docker rmi image1
```

Verify that the image has been removed:

```bash
docker images image2
```

<img width="1681" height="47" alt="image" src="https://github.com/user-attachments/assets/ebe6d2a3-938e-4a71-b85e-e91aa814a985" />


## 10. Loading and Verifying the Image

Restore the image:

```bash
docker load -i lab-image.tar
```

Verify that the image exists:

```bash
docker image inspect image2
```
<img width="1009" height="926" alt="image" src="https://github.com/user-attachments/assets/b12064cd-21d1-4014-be76-eb15d34dbb3a" />

