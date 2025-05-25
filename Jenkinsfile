pipeline {
    agent any

    environment {
        IMAGE_NAME = "fatma21/python_pipeline"
    }

    stages {
        stage("Build Docker image") {
            steps {
                sh "docker build -t ${IMAGE_NAME}:v${BUILD_NUMBER} ."
            }
        }

        stage("Login to DockerHub") {
            steps {
                withCredentials([usernamePassword(credentialsId: 'dockerhub', usernameVariable: 'DOCKER_USERNAME', passwordVariable: 'DOCKER_PASSWORD')]) {
                    sh "echo $DOCKER_PASSWORD | docker login -u $DOCKER_USERNAME --password-stdin"
                }
            }
        }

        stage("Push Docker image") {
            steps {
                sh "docker push ${IMAGE_NAME}:v${BUILD_NUMBER}"
            }
        }
    }
}

