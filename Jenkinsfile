pipeline {
   agent { label 'slave3' }
    environment {
    DOCKERHUB_CREDENTIALS = credentials('Docker')
    }
    stages { 
        stage('SCM Checkout') {
            steps{
        git branch: 'main', url: 'https://github.com/poornendra002/assign22-12.git'
            }
        }

        stage('Build stage') {
            steps {  
                sh '''
                docker build -t poornendra/repo:ngin .
                '''
            }
        }
        stage('login to dockerhub') {
            steps{
                sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
            }
        }
        stage('push image') {
            steps{
                sh 'docker push valaxy/nodeapp:$BUILD_NUMBER'
            }
        }
}
}
