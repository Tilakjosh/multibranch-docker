pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh 'docker build -t image2 .'
            }
        }
        stage ("Tag") {
            steps {
                sh 'docker tag image2 tilakjosh45/paytm:bus'
            }
        }
        stage('push') {
            steps {
                script {
                  withDockerRegistry(credentialsId: 'dockerhub') {
                    sh "docker push tilakjosh45/paytm:bus"
            }
        }
    }
        }
        stage ("Deploy") {
            steps {
                sh 'docker run -itd --name bus-app -p 2222:80 tilakjosh45/paytm:bus'
            }
        }
    }
}
