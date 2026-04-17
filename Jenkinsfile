pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Verify') {
            steps {
                script {
                    if (fileExists('index.html')) {
                        echo "index.html found!"
                    } else {
                        error "index.html not found!"
                    }
                }
            }
        }
        stage('Deploy') {
            steps {
                echo "Deploy step: index.html is ready."
            }
        }
    }
    post {
        success {
            echo 'Pipeline completed successfully!'
        }
        failure {
            echo 'Pipeline failed. Check logs.'
        }
    }
}
