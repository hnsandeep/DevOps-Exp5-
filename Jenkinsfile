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
                script {
                    // Ensure target folder exists
                    bat 'if not exist C:\\Apache24\\htdocs\\myapp mkdir C:\\Apache24\\htdocs\\myapp'
                    
                    // Copy files from Jenkins workspace to Apache htdocs
                    bat 'xcopy /Y /E "%WORKSPACE%\\*" "C:\\Apache24\\htdocs\\myapp\\"'
                }
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
