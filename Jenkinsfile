pipeline {
    agent any

    stages {
        stage('Build Docker Image') {
            steps {
                bat 'docker build -t raghu045/sample-app:v1 .'
            }
        }

        stage('Push Docker Image') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'dockerhub-creds', usernameVariable: 'USER', passwordVariable: 'PASS')]) {
                    // Double quotes (") allow Jenkins to instantly replace ${PASS} and ${USER} before running the batch block
                    bat "echo ${PASS}| docker login -u ${USER} --password-stdin"
                    bat 'docker push raghu045/sample-app:v1'
                }
            }
        }
    }
}
