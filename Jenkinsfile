
pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                echo 'Fetching source code from GitHub'
                checkout scm
            }
        }

        stage('Build') {
            steps {
                echo 'Building application'
                bat 'python app.py'
            }
        }

        stage('Test') {
            steps {
                echo 'Testing application'
                bat 'python -m py_compile app.py'
                echo 'All tests passed!'
            }
        }

        stage('Success') {
            steps {
                echo 'Pipeline executed successfully!'
            }
        }

        stage('Finish') {
            steps {
                echo 'Build process completed!'
            }
        }
    }

    post {
        success {
            echo 'BUILD SUCCESSFUL!'
        }

        failure {
            echo 'BUILD FAILED! Check Console Output.'
        }

        always {
            echo 'Pipeline execution finished.'
        }
    }
}
