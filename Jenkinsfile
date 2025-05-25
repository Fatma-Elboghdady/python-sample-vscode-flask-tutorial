pipeline {
    agent any

    environment {
        XYZ = 'ITI ITI ITI'
    }

    stages {
        stage("build Docker image") {
            steps {
                sh "docker build -t fatma21/python_piplin:v${BUILD_NUMBER} ."
            }
        }
        stage("Push Docker image") {
            steps {
                withCredentials([usernamePassword(credentialsId: 'dockerhub', usernameVariable: 'DOCKER_USERNAME', passwordVariable: 'DOCKER_PASSWORD')]) {
                    sh "echo $DOCKER_PASSWORD | docker login -u $DOCKER_USERNAME --password-stdin"
                    sh "docker push fatma21/python_piplin:v${BUILD_NUMBER}"
                }
            }
        }
    }
}
