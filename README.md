# DevOps Capstone Project

This project demonstrates a complete **CI/CD pipeline using GitHub, Jenkins, Docker, and AWS EC2**.

Whenever a developer pushes code to GitHub, a **GitHub Webhook automatically triggers Jenkins**, which builds a Docker image, pushes it to **DockerHub**, and deploys the application in a Docker container.

---

## Architecture

Developer → GitHub → Jenkins → Docker Build → DockerHub → Deploy Container → Application

---

## Technologies Used

* GitHub (Source Code Management)
* Jenkins (CI/CD Automation)
* Docker (Containerization)
* DockerHub (Image Registry)
* AWS EC2 (Cloud Infrastructure)
* Python Flask (Sample Application)

---

## CI/CD Pipeline Flow

1. Developer pushes code to the GitHub repository
2. GitHub webhook triggers the Jenkins pipeline automatically
3. Jenkins pulls the latest code from GitHub
4. Jenkins builds the Docker image
5. Docker image is pushed to DockerHub
6. Jenkins deploys the container on the EC2 server
7. Application becomes accessible through the browser

---

## Application Setup

Clone the repository

git clone https://github.com/Raakeshgideon/Devops-capstone.git

cd Devops-capstone

---

## Run Application with Docker (Manual Method)

Build Docker Image

docker build -t capstone-app .

Run Container

docker run -d -p 5000:5000 capstone-app

---

## Access the Application

Open the browser and navigate to

http://<EC2_PUBLIC_IP>:5000

Example:

http://65.0.96.116:5000

---
