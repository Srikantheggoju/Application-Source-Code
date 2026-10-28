pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                echo 'Source already checked out by Jenkins SCM'
            }
        }

        stage('Workspace Validation') {
            steps {
                sh 'pwd'
                sh 'ls -la'
            }
        }

        stage('Application Validation') {
            steps {
                echo 'Application files are available'
                sh 'cat requirements.txt'
            }
        }
    }

    post {
        success {
            echo 'Pipeline executed successfully'
        }

        failure {
            echo 'Pipeline execution failed'
        }
    }
}
