pipeline {
    agent any

    environment {
        IMAGE_NAME = "srikantheggoju/flask-app"
    }

    stages {

        stage('Checkout') {
            steps {
                echo 'Source already checked out by Jenkins SCM'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t $IMAGE_NAME:${BUILD_NUMBER} .'
            }
        }

        stage('Push Docker Image') {
            steps {
                withCredentials([usernamePassword(
                    credentialsId: 'dockerhub',
                    usernameVariable: 'USER',
                    passwordVariable: 'PASS'
                )]) {

                    sh '''
                    docker login -u $USER -p $PASS
                    docker push $IMAGE_NAME:${BUILD_NUMBER}
                    '''
                }
            }
        }
    }

    post {
        success {
            echo 'Docker image pushed successfully'
        }
        failure {
            echo 'Pipeline failed'
        }
    }
}
