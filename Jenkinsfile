@Library('jenkins-shared-library') _

pipeline {
    agent any

    environment {
        IMAGE_NAME = 'fatma21/python-task1'
    }

    stages {
        stage('Build Docker Image') {
            steps {
                buildDockerImage(env.IMAGE_NAME)
            }
        }

        stage('Push Docker Image') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'dockerhub-cred', usernameVariable: 'DOCKER_USERNAME', passwordVariable: 'DOCKER_PASSWORD')]) {
                    pushDockerImage(env.IMAGE_NAME)
                }
            }
        }
    }
}
