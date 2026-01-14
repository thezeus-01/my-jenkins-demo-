pipeline {
    agent any

    environment {
        APP_NAME = "newdem-app"
    }

    stages {

        stage('Checkout') {
            steps {
                echo "Source code already checked out by SCM"
                sh 'ls -la'
            }
        }

        stage('Build') {
            steps {
                echo "Building the application..."
                sh '''
                    echo "Simulating build process"
                    mkdir -p build
                    echo "Build successful for $APP_NAME" > build/build.txt
                '''
            }
        }

        stage('Test') {
            steps {
                echo "Running tests..."
                sh '''
                    echo "Running sample test"
                    test -f build/build.txt
                '''
            }
        }

        stage('Archive') {
            steps {
                echo "Archiving build artifacts"
                archiveArtifacts artifacts: 'build/**', fingerprint: true
            }
        }

        stage('Deploy') {
            steps {
                echo "Deploying application..."
                sh '''
                    echo "Deploy step completed"
                '''
            }
        }
    }

    post {
        success {
            echo "Pipeline completed successfully"
        }
        failure {
            echo "Pipeline failed"
        }
        always {
            echo "Pipeline execution finished"
        }
    }
}
