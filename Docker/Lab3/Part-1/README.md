# Lab-3 part-1 "Creating docker image & building the app inside the container" 

## 1. Cloning Repo
```Linux
git clone https://github.com/Ibrahim-Adel15/CalculatorMavenApp.git
```
<img width="788" height="366" alt="image" src="https://github.com/user-attachments/assets/0963921f-a539-454f-a18a-4d89f00d9709" />

## 2. Creating Dockerfile
```Linux
vim Dockerfilevim
```
<img width="487" height="250" alt="image" src="https://github.com/user-attachments/assets/8db5152f-0a11-4d67-ad5c-fec4cf40ff36" />

## 3. Building Docker Image
```Linux
docker build -t lab3 .
```
<img width="1891" height="411" alt="image" src="https://github.com/user-attachments/assets/b0370160-efba-4b16-9507-a783db1fec09" />

## 4. Running container
```Linux
docker run -d --name cont1 -p 8085:8080 lab3
docker ps -a
```
<img width="1041" height="49" alt="image" src="https://github.com/user-attachments/assets/3f2dc60f-8677-45e7-8d3c-46af9be9cfe3" />

## 5. Deleting Docker Image & Container
```Linux
docker rm cf9
docker rmi lab3:latest
```

