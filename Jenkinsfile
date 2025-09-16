pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh 'docker build -t image3 .'
            }
        }
        stage ("Tag") {
            steps {
                sh 'docker tag image3 tilakjosh45/paytm:movie'
            }
        }
        stage('push') {
            steps {
                script {
                  withDockerRegistry(credentialsId: 'dockerhub') {
                    sh "docker push tilakjosh45/paytm:movie"
            }
        }
    }
        }
        
        stage ("Deploy") {
            steps {
                sh 'docker run -itd --name movie-app -p 3333:80 tilakjosh45/paytm:movie'
            }
        }
    }
}
