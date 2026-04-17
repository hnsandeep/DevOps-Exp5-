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
        stage('Deploy') {
            steps {
                // Archive the file so Jenkins shows it in build artifacts
                archiveArtifacts artifacts: 'index.html', fingerprint: true
                echo "index.html archived as build artifact."
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
