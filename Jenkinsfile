pipeline {
    agent any

    environment {
        DOCKER_IMAGE = "raakeshdevops/capstone-app"
        DOCKER_SERVER = "ubuntu@13.234.237.13"
    }

    stages {

        stage('Build Docker Image') {
            steps {
                sh '''
                ssh $DOCKER_SERVER "docker build -t $DOCKER_IMAGE:latest ."
                '''
            }
        }

        stage('Login to DockerHub') {
            steps {
                withCredentials([usernamePassword(
                    credentialsId: 'dockerhub-creds',
                    usernameVariable: 'DOCKER_USER',
                    passwordVariable: 'DOCKER_PASS'
                )]) {
                    sh '''
                    ssh $DOCKER_SERVER "
                    echo $DOCKER_PASS | docker login -u $DOCKER_USER --password-stdin
                    "
                    '''
                }
            }
        }

        stage('Push Image') {
            steps {
                sh '''
                ssh $DOCKER_SERVER "docker push $DOCKER_IMAGE:latest"
                '''
            }
        }

        stage('Deploy Container') {
            steps {
                sh '''
                ssh $DOCKER_SERVER "
                docker stop capstone || true
                docker rm capstone || true
                docker run -d -p 5000:5000 --name capstone $DOCKER_IMAGE:latest
                "
                '''
            }
        }
    }
}
