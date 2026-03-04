## Application Setup

Clone the repository

git clone https://github.com/Raakeshgideon/Devops-capstone.git

cd Devops-capstone

## Run Application with Docker

Build Docker Image

docker build -t capstone-app .

Run Container

docker run -d -p 5000:5000 capstone-app

Open browser

http://<EC2_PUBLIC_IP>:5000
