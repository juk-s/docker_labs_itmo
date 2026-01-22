# Домашнее задание Kubernetes
Корсакова Юлия  

## Описание выполненных шагов
### 1. Создана структура проекта
<img width="302" height="111" alt="image" src="https://github.com/user-attachments/assets/b8de751c-7de1-49f3-bc96-dd87093dd02c" />

### 2. Написан html файл, содержащий текст "Hello World"  
### 3. Написан Dockerfile, в котором  
   * `FROM python:3.14-alpine` - используется базовый образ Python
   * `RUN adduser -D -u 10001 appuser` - создается пользователь с uid=10001
   * `WORKDIR /app` - создается каталог `/app` и назначается как WORKDIR
   * `COPY hello.html /app/` - копируется файл hello.html в рабочую директорию
   * `USER appuser` - происходит переключение на созданного пользователя
   * `EXPOSE 8000` - настроен порт, который слушает приложение
   * `CMD ["python", "-m", "http.server", "8000"]` - запускается команда для запуска веб сервера
### 4. Собран docker image: 
`docker build -t hello-app:1.0.0 .`  

<img width="648" height="45" alt="image" src="https://github.com/user-attachments/assets/9bd74e29-91b2-44a4-a541-a2b96a0f78f1" />

### 5. Запущен docker контейнер 
`docker run -d -p 8000:8000 hello-app:1.0.0`  

Проверка работы приложения:  
<img width="1283" height="725" alt="image" src="https://github.com/user-attachments/assets/8fe0db06-8996-435e-94a0-7597c0292e3b" />

### 6. Docker image переименован с использованием имени пользователя docker hub
### 7. Image размещен на docker hub 
`docker push jukuser/hello-app:1.0.0`   

<img width="1422" height="234" alt="image" src="https://github.com/user-attachments/assets/8b56d5dc-0f22-4347-89ed-b26b38cc73eb" />

### 8. Создан Kubernetes Deployment манифест 
`hello-app/web-deployment.yaml`
### 9. Запуск кластера 
`minikube start --drive=docker`
### 10. Установка манифеста в кластер kubernetes 
`kubectl apply -f web-deployment.yaml`  

<img width="659" height="60" alt="image" src="https://github.com/user-attachments/assets/e8043c0a-b37d-40c0-ab78-ef95915976df" />

### 11. Создан Service NodePort для Deployment
`hello-app/web-nodeport-service.yaml`  

<img width="625" height="64" alt="image" src="https://github.com/user-attachments/assets/7c753155-cfef-412e-9d00-ccc9d7b8da47" />

### 12. Результат curl показывающий доступ к приложению
<img width="1120" height="617" alt="image" src="https://github.com/user-attachments/assets/50225387-52d4-4e3c-ad39-ea86062df2dc" />

<img width="1279" height="581" alt="image" src="https://github.com/user-attachments/assets/402dc2ec-9916-45a5-85e2-7ea5ae6974bc" />







