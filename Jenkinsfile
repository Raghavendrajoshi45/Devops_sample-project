pipeline {
    agent any

    stages {

        stage('Clone') {
            steps {
                git 'https://github.com/Raghavendrajoshi45/Devops-sample-project.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t raghu045/sample-app:v1 .'
            }
        }

        stage('Push Docker Image') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'dockerhub-creds', usernameVariable: 'USER', passwordVariable: 'PASS')]) {
                    sh 'echo $PASS | docker login -u $USER --password-stdin'
                    sh 'docker push raghu045/sample-app:v1'
                }
            }
        }
    }
}
