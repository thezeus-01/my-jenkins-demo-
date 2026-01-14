pipeline {
    agent any

    environment {
        APP_NAME = "newdem-app"
        BUILD_DIR = "build"
    }

    stages {

        stage('Initialize') {
            steps {
                echo "Initializing pipeline"
                sh 'date'
                sh 'whoami'
                sh 'pwd'
            }
        }

        stage('Checkout') {
            steps {
                echo "Source already checked out from SCM"
                sh 'ls -la'
            }
        }

        stage('Build') {
            steps {
                echo "Starting build process"
                sh '''
                    mkdir -p ${BUILD_DIR}
                    echo "Application: ${APP_NAME}" > ${BUILD_DIR}/app.txt
                    echo "Build Time: $(date)" >> ${BUILD_DIR}/app.txt
                    echo "Build completed successfully"
                '''
            }
        }

        stage('Test') {
            steps {
                echo "Running tests"
                sh '''
                    if [ -f ${BUILD_DIR}/app.txt ]; then
                        echo "Test passed: build artifact exists"
                    else
                        echo "Test failed"
                        exit 1
                    fi
                '''
            }
        }

        stage('Quality Check') {
            steps {
                echo "Performing quality checks"
                sh '''
                    wc -l ${BUILD_DIR}/app.txt
                    cat ${BUILD_DIR}/app.txt
                '''
            }
        }

        stage('Archive Artifacts') {
            steps {
                echo "Archiving build artifacts"
                archiveArtifacts artifacts: 'build/**', fingerprint: true
            }
        }

        stage('Deploy') {
            steps {
                echo "Simulated deployment"
                sh '''
                    echo "Deploying ${APP_NAME}"
                    sleep 2
                    echo "Deployment successful"
                '''
            }
        }
    }

    post {
        success {
            echo "✅ Pipeline completed successfully"
        }
        always {
            echo "Pipeline execution finished"
        }
    }
}
