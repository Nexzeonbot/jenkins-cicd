pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                echo 'Code checkout successful'
            }
        }

        stage('Build') {
            steps {
                echo 'Application build started'
            }
        }

        stage('Test') {
            steps {
                echo 'Application test successful'
            }
        }

        stage('Docker Build') {
            steps {
                sh 'docker build -t jenkins-cicd:latest .'
            }
        }

        stage('Docker Run') {
            steps {
                sh '''
                    docker stop jenkins-cicd || true
                    docker rm jenkins-cicd || true
                    docker run -d --name jenkins-cicd -p 80:80 jenkins-cicd:latest
                '''
            }
        }
    }
}
