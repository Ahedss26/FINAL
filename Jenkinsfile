pipeline{
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building...'
                sh 'docker build -t ahedfinal .'   

            }
        }
        stage('login docker hub') {
            steps {
                echo 'logging in...'
                withCredentials([usernamePassword(credentialsId: 'dockerhub', passwordVariable: 'DOCKER_HUB_PASSWORD', usernameVariable: 'DOCKER_HUB_USERNAME')]) {
                    sh 'echo $DOCKER_HUB_PASSWORD | docker login -u $DOCKER_HUB_USERNAME --password-stdin'
            }
        }
        stage('docker push') {
            steps {
                echo 'pushing image...'
                sh 'docker push ahed2604/final:latest'

            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying...'
            }
        }
    }
}