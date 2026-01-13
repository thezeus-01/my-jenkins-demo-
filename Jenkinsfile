pipeline {
    agent any

    environment {
        GIT_REPO = 'https://github.com/USERNAME/REPO_NAME.git'
        BRANCH   = 'main'
    }

    stages {

        stage('Checkout') {
            steps {
                echo "Cloning source code from GitHub..."
                git branch: "${BRANCH}", url: "${GIT_REPO}"
            }
        }

        stage('Build') {
            steps {
                echo "Building the project..."
                sh '''
                    echo "Build step running"
                    ls -la
                '''
            }
        }

        stage('Test') {
            steps {
                echo "Running tests..."
                sh '''
                    echo "Test step running"
                '''
            }
        }

        stage('Deploy') {
            steps {
                echo "Deploying application..."
                sh '''
                    echo "Deploy step running"
                '''
            }
        }
    }

    post {
        success {
            echo "Pipeline executed successfully"
        }
        failure {
            echo "Pipeline failed"
        }
    }
}

