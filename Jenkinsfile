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
                echo 'Building Docker image...'
                bat 'docker build -t shreyyvicharee/myflaskapp:latest .'
            }
        }

        stage('Test') {
            steps {
                echo 'Running Flask app test...'
                // optional sanity test
                bat 'docker run --rm -d -p 5000:5000 shreyyvicharee/myflaskapp:latest'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Pushing image to Docker Hub...'
                withCredentials([usernamePassword(credentialsId: 'dockerhub-creds', usernameVariable: 'DOCKER_USER', passwordVariable: 'DOCKER_PASS')]) {
                    bat 'docker login -u shreyyvicharee -p iw@535am
                    bat 'docker push shreyyvicharee/myflaskapp:latest'
                }
            }
        }
    }

    post {
        success {
            echo ' Pipeline completed successfully!'
        }
        failure {
            echo ' Pipeline failed. Check logs for details.'
        }
    }
}

