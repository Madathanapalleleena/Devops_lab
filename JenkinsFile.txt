pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                echo 'Checking out source code...'
                checkout scm
            }
        }

        stage('Build') {
            steps {
                echo 'Building the application...'

                bat '''
                    echo Current directory:
                    cd

                    echo.
                    echo Java version:
                    java --version

                    echo.
                    echo Git version:
                    git --version

                    echo.
                    echo Application files:
                    dir src
                '''
            }
        }

        stage('Test') {
            steps {
                bat '''
                    if exist src\\index.html (
                        echo Application file found!
                        echo Test passed!
                    ) else (
                        echo Application file NOT found!
                        exit /b 1
                    )
                '''
            }
        }

        stage('Finish') {
            steps {
                echo 'Build and test completed successfully!'
            }
        }
    }

    post {
        success {
            echo 'PIPELINE SUCCESS'
        }

        failure {
            echo 'PIPELINE FAILED'
        }
    }
}
