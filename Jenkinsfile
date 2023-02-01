pipeline {
    agent any
    environment {
        DOCKERHUB_CREDENTIALS = credentials('Docker_Cred') 
    }
    stages {
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t rahilgulaliyev/scramjet .'
            }
        }
        stage('Login DockerHub') {
            steps {
                sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
            }
        }
        stage('Push Docker Image') {
            steps {
                sh 'docker push rahilgulaliyev/scramjet:latest'
            }
        }
    }
    post {
      always {
        sh 'docker logout'
      }
    }
}

