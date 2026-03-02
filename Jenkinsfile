pipeline {
    agent any

    environment {
        DOCKER_IMAGE = "raakeshdevops/capstone-app"
    }

        stage('Clone') {
            steps {
                git credentialsId: 'github-creds',
                    url: 'https://github.com/Raakeshgideon/Devops-capstone/.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t $DOCKER_IMAGE:latest .'
            }
        }

        stage('Login to DockerHub') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'dockerhub-creds',
                                                 usernameVariable: 'raakeshdevops',
                                                 passwordVariable: 'Raakesh@24')]) {
                    sh 'echo $DOCKER_PASS | docker login -u $DOCKER_USER --password-stdin'
                }
            }
        }

        stage('Push Image') {
            steps {
                sh 'docker push $DOCKER_IMAGE:latest'
            }
        }
    }
}


