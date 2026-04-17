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
                        echo "✅ index.html found!"
                    } else {
                        error "❌ index.html not found!"
                    }
                }
            }
        }
        stage('Build') {
            steps {
                echo "No build required for static HTML."
            }
        }
        stage('Deploy') {
            steps {
                bat '''
                copy index.html "C:\\Apache24\\htdocs\\index.html"
                '''
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
