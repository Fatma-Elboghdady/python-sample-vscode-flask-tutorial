pipeline{
    agent any
    environment{
        XYZ='ITI ITI ITI'
    }
    stages{
        stage("build Docker image"){
            steps{
                sh "docker build -t fatma21/python_piplin:v${BUILD_NUMBER} ."
            }
        }
        stage("Push Docker image"){
            steps{
                sh "docker push fatma21/python_piplin:v${BUILD_NUMBER}"
            }
        }
    }
}
