# Lab-3 part-2 "Creating docker image & building the app locally" 

## 1. Cloning Repo
```Linux
git clone https://github.com/Ibrahim-Adel15/CalculatorMavenApp.git
```
<img width="788" height="366" alt="image" src="https://github.com/user-attachments/assets/0963921f-a539-454f-a18a-4d89f00d9709" />


## 2. Creating Dockerfile
```Linux
vim Dockerfilevim
```
<img width="445" height="218" alt="image" src="https://github.com/user-attachments/assets/7ca2903c-6357-43c1-b128-540cf4235c37" />


## 3. Building Docker Image
```Linux
docker build -t lab3_part2 .
```
<img width="1095" height="414" alt="image" src="https://github.com/user-attachments/assets/3c88e844-a989-43be-b5f3-716b33d7deda" />


## 4. Running container
```Linux
docker run -d --name cont2 -p 8085:8080 lab3-part2
docker ps -a
```
<img width="1082" height="50" alt="image" src="https://github.com/user-attachments/assets/4b8be776-fa3e-4983-a460-e7b8dda3539f" />


## 5. Deleting Docker Image & Container
```Linux
docker rm 64f
docker rmi lab3_part2:latest
```

