pipeline {
    agent any

    environment {
        IMAGE_NAME = "yourdockerhub/flask-app"
    }

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main',
                url: 'https://github.com/Srikantheggoju/flask-app.git'
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
}
