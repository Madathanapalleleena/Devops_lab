pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                echo 'Fetching source code'
                checkout scm
            }
        }

        stage('Build') {
            steps {
                echo 'Building application'
                bat 'python app.py'
            }
        }

        stage('Success') {
            steps {
                echo 'Pipeline executed successfully!'
            }
        }
    }
}
