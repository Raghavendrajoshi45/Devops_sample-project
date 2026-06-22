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
                    sh 'echo $PASS | docker login -u $USER --password-stdin'
                    sh 'docker push raghu045/sample-app:v1'
                }
            }
        }
    }
}
