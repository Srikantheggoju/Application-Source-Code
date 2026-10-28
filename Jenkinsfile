pipeline {
    agent any

    environment {
        IMAGE_NAME = "Srikanth/flask-app"
    }

    stages {

        stage('Checkout') {
            steps {
                echo 'Source already checked out by Jenkins SCM'
            }
        }

        stage('Docker Version') {
            steps {
                sh 'docker --version'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t $IMAGE_NAME:${BUILD_NUMBER} .'
            }
        }
    }

    post {
        success {
            echo 'Docker image build successful'
        }

        failure {
            echo 'Build failed'
        }
    }
}
