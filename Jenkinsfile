pipeline {
   agent { label 'slave3' }
    environment {
    DOCKERHUB_CREDENTIALS = credentials('Docker')
    }
   stages {
        stage('Build stage') {
            steps {  
                sh '''
                docker build -t poornendra/repo:ngin .
                docker run -d --name nginassignment1 -p 9000:80 poornendra/repo:ngin  
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
                sh 'docker push poornendra/repo:ngin'
            }
        }
}
}
