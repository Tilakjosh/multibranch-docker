pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh 'docker build -t image1 .'
            }
        }
        stage ("Tag") {
            steps {
                sh 'docker tag image1 tilakjosh45/paytm:bank'
            }
        }
        stage('push') {
            steps {
                script {
                  withDockerRegistry(credentialsId: 'dockerhub') {
                    sh "docker push tilakjosh45/paytm:bank"
            }
        }
    }
        }
        
        stage ("Deploy") {
            steps {
                sh 'docker run -itd --name bank-app -p 1111:80 tilakjosh45/paytm:bank'
            }
        }
    }
}
