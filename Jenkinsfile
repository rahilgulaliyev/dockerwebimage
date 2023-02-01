pipeline {
    agent any
    environment {
        DOCKER_HUB = credentials( 'Docker_Cred' ) 
    }
    stages {
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t rahil/scramjet .'
            }
        }
        stage('Push Docker Image') {
            steps {
                sh 'docker login -u "$DOCKER_HUB_USERNAME" -p "$DOCKER_HUB_PASSWORD"'
                sh 'docker tag rahil/scramject "$DOCKER_HUB_USERNAME"/rahil/scramjet:latest'
                sh 'docker push "$DOCKER_HUB_USERNAME"/rahil/scramjet:latest'
            }
        }
    }
}

