pipeline {
    agent any

    stages {
        stage('Info') {
            steps {
                echo "Branch Name: ${env.BRANCH_NAME}"
                echo "Build Number: ${env.BUILD_NUMBER}"
            }
        }

        stage('Build') {
            steps {
                echo "Building on branch ${env.BRANCH_NAME}"
                sh 'sleep 2'
            }
        }

        stage('Test') {
            steps {
                echo "Testing on branch ${env.BRANCH_NAME}"
            }
        }
    }

    post {
        success {
            echo "Pipeline SUCCESS on ${env.BRANCH_NAME}"
        }
    }
}
