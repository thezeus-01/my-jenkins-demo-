pipeline {
    agent any

    stages {

        stage('Build') {
            steps {
                echo "Build stage started"
                sh '''
                    echo "Simulating failure..."
                    exit 1
                '''
            }
        }

        stage('Test') {
            steps {
                echo "This stage should NEVER run"
            }
        }
    }

    post {
        failure {
            echo "❌ Pipeline failed as expected"
        }
    }
}
