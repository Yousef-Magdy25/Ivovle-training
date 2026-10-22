# Lab-1 Building & testing the calculator app with maven 

## 1. Installation 
```Linux
sudo apt update
sudo apt install -y openjdk-17-jdk maven   # Ubuntu
```

```Linux
java --version
```
openjdk 17.0.20.1 2026-08-18

```Linux
mvn --version
```
Apache Maven 3.9.12

## Cloning Repo
```Linux
git clone https://github.com/Ibrahim-Adel15/CalculatorMavenApp.git
```
<img width="788" height="366" alt="image" src="https://github.com/user-attachments/assets/0963921f-a539-454f-a18a-4d89f00d9709" />

## Testing the code
```Linux
mvn test
```
<img width="1209" height="347" alt="image" src="https://github.com/user-attachments/assets/90a74c40-969d-496f-b7c0-8a46842d7b5e" />

## Compiling
```Linux
mvn package
```
<img width="773" height="155" alt="image" src="https://github.com/user-attachments/assets/9676ac96-8487-425a-8824-dc76ec37c508" />
<img width="646" height="972" alt="image" src="https://github.com/user-attachments/assets/6ceefcbd-7358-4a58-aed5-667205555c5f" />

## Results
```Linux
java -jar target/calculator.jar
```
<img width="232" height="150" alt="image" src="https://github.com/user-attachments/assets/f986bdae-ab9c-43b9-9baa-9b58f408d895" />
