pipeline {
    agent any

    environment {
        IMAGE_NAME = "deploydockerapp"
        CONTAINER_NAME = "deploy_container"
    }

    stages {
        stage('Clone Repository') {
            steps {
                git branch: 'main', credentialsId: '486ba5f3-a7f8-4284-bb3b-fb4236bdaaf9', url: 'https://github.com/ANGELMTZ59/DeployDockerApp.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    sh 'docker build -t $IMAGE_NAME .'
                }
            }
        }

        stage('Run Docker Container') {
            steps {
                script {
                    sh 'docker stop $CONTAINER_NAME || true && docker rm $CONTAINER_NAME || true'
                    sh 'docker run -d --name $CONTAINER_NAME -p 5000:5000 $IMAGE_NAME'
                }
            }
        }
    }
}