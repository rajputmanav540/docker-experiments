# Experiment Portfolio: 10 Projects with Docker, Streamlit, and More

Welcome to my experiment portfolio! This repository showcases **10 unique projects** that demonstrate my expertise in **Docker**, **Streamlit**, **Machine Learning (ML)**, **MySQL**, **Networking**, and **AWS EC2**. Each project is designed to solve real-world problems, leveraging cutting-edge technologies and best practices.

Below, you’ll find a detailed description of each project, along with code snippets and deployment instructions. Let’s dive in! 🐳🖥️

---

## Table of Contents 💑

1. [Docker Basics: Hello World](1.Hello_World/Docker_Basics)
2. [Streamlit App Using Docker](2.Streamlit_Docker/Dockers_Streamlit)
3. [ML Model Using Docker](3.StreamlitModel_Docker/StreamlitModel_Docker)
4. [MySQL Using Docker](4.Docker_Mysql)
5. [Networking Using Docker](5.Docker_network/Docker_Network)
6. [Full Stack App Using Docker](6.Docker_fullstack/Docker_FullStack)
7. [Docker Volume](7.Docker_volume/Docker_volume)
8. [ML Monitoring Dashboard with Evidently and Streamlit](8.Stream_evidently/Streamlit_evidently)
9. [Streamlit App on AWS EC2](10.Docker_EC2)
10. [Streamlit Using Evidently](9.Minikube-and-Kucetl/Minikube-and-Kucetl)

---

## 1. Docker Basics: Hello World 🐳

### Description
This project introduces the basics of Docker by creating a simple Python script that prints "Hello World!" inside a Docker container. It covers the fundamentals of Docker, including building and running containers.

### Code
```bash
# Dockerfile
FROM python:3.9-slim
WORKDIR /app
COPY app.py /app
CMD ["python", "app.py"]
```

```bash
# app.py
print("Hello World! 🐳")
```

Deployment

```bash
docker build -t hello-world .
docker run hello-world
```

## 2. Streamlit App Using Docker 🐍

### Description
This project demonstrates how to containerize a Streamlit app using Docker. The app provides an interactive interface for data visualization and analysis.

```bash
# Dockerfile
FROM python:3.9
WORKDIR /app
COPY . .
RUN pip install -r requirements.txt
CMD ["streamlit", "run", "app.py", "--server.port=8501", "--server.address=0.0.0.0"]
```

Deployment

```bash
docker build -t streamlit-app .
docker run -p 8501:8501 streamlit-app
```

## 3. ML Model Using Docker 🤖

### Description
This project deploys a Machine Learning model using Docker. The model is trained on a dataset and served via a Streamlit app for real-time predictions.

```bash
# Dockerfile
FROM python:3.9-slim
WORKDIR /app
COPY . .
RUN pip install -r requirements.txt
CMD ["streamlit", "run", "app.py", "--server.port=8501", "--server.address=0.0.0.0"]
```

Deployment

```bash
docker build -t ml-model .
docker run -p 8501:8501 ml-model
```

## 4. MySQL Using Docker 🟢

### Description
This project sets up a MySQL database inside a Docker container. It includes a sample SQL script to create a database and insert data.

```bash
# Dockerfile
FROM mysql:latest
ENV MYSQL_ROOT_PASSWORD=root
COPY database.sql /docker-entrypoint-initdb.d/
```

Deployment

```bash
docker build -t mysql-db .
docker run -d --name mysql-container mysql-db
```

## 5. Networking Using Docker 🌐

### Description
This project explores Docker Networking by creating a custom bridge network and connecting multiple containers to it.

```bash
# Create a custom network
docker network create my_network

# Run containers on the network
docker run -d --name container1 --network my_network nginx
docker run -d --name container2 --network my_network nginx
```

Deployment

```bash
docker network inspect my_network
```

## 6. Full Stack App Using Docker 🖥️

### Description
This project deploys a full-stack application using Docker. It includes a PostgreSQL database and a Streamlit frontend, connected via a custom Docker network.

```bash
# Dockerfile for Streamlit
FROM python:3.9
WORKDIR /app
COPY . .
RUN pip install -r requirements.txt
CMD ["streamlit", "run", "app.py", "--server.port=8501", "--server.address=0.0.0.0"]
```

Deployment

```bash
docker build -t fullstack-app .
docker run -d --name fullstack-container fullstack-app
```

## 7. Docker Volume 💾

### Description
This project demonstrates how to use Docker Volumes for persistent data storage. It includes examples of attaching volumes to containers and sharing data between them.

```bash
# Create a Docker volume
docker volume create my_volume

# Attach volume to a container
docker run -it -v my_volume:/data ubuntu
```

Deployment

```bash
docker volume inspect my_volume
```

## 8. ML Monitoring Dashboard with Evidently and Streamlit 📊

### Description
This project creates an ML Monitoring Dashboard using Evidently and Streamlit. It visualizes data drift and model performance metrics.

```bash
# Run Streamlit app
streamlit run app.py
```

## 9. Streamlit App on AWS EC2 ☁️

### Description
This project deploys a Streamlit app on an AWS EC2 instance using Docker. It includes steps for setting up the EC2 instance and running the app.

```bash
# Connect to EC2 instance
ssh -i /path/to/key.pem ec2-user@public-ip

# Run Docker container
docker run -d -p 8501:8501 streamlit-app
```

## 10. Streamlit Using Evidently

### Description
This project demonstrates how to integrate **Streamlit** with **Evidently**, an open-source tool for monitoring and analyzing machine learning models.

```bash
pip install streamlit evidently pandas
```

Run the Streamlit app:

```bash
streamlit run app.py
```

🚀 **Enhance your ML model monitoring with Streamlit and Evidently!**
