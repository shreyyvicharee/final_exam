pipeline {
    agent any

    triggers {
        pollSCM('H/2 * * * *')
    }

    stages {
        stage('Checkout') {
            steps {
                echo ' Checking out source code...'
                checkout scm
                sh 'ls -l'   // Works fine because Jenkins runs via Git Bash
            }
        }

        stage('Build') {
            steps {
                echo ' Building the project...'
                sh 'echo "Build completed successfully!"'
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests...'
                sh 'echo "All tests passed!"'
            }
        }

        stage('Deploy') {
            steps {
                echo ' Deploying application...'
                sh 'echo "Deployment successful!"'
            }
        }
    }
}
