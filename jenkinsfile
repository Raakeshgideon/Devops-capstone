pipeline {
    agent any

    stages {
        stage('Clone') {
            steps {
                echo 'Cloning code...'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t capstone-app .'
            }
        }

        stage('Run Container') {
            steps {
                sh '''
                docker stop capstone || true
                docker rm capstone || true
                docker run -d -p 5000:5000 --name capstone capstone-app
                '''
            }
        }
    }
}
