pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                git 'https://github.com/praveen-2205/devops-cicd-lab'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t praveen/2023bcs0115 .'
            }
        }

        stage('Login DockerHub') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'dockerhub', usernameVariable: 'USER', passwordVariable: 'PASS')]) {
                    sh 'echo $PASS | docker login -u $USER --password-stdin'
                }
            }
        }

        stage('Push Image') {
            steps {
                sh 'docker push praveen/2023bcs0115'
            }
        }

    }
}
