pipeline {
    agent { label 'master' }
    environment {
        DOCKERHUB_CREDENTIALS=credentials('dockerhub-paulogugas')
    }

    stages {

        stage('Checkout') {
            steps{
                git branch: 'git@github.com:gugas1250/jenkins-dockerhub1.git'
            }
        }

        stage('Build') {
            steps{
                sh 'docker build -t devops21:latest'
            }
        }

        stage('Login') {
            steps {
                sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
            }
        }

        stage('ImageTag') {
            steps {
                sh 'docker tag devops14:latest vakhobdevops/devops14-docker:version2'
            }
        }

        stage('Push') {
            steps {
                sh 'docker push paulogugas/devops21-docker'
            }
        }
    }

    post {
        always {
            sh 'docker logout'
        }
    }
}
