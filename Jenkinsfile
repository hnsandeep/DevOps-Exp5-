pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                // Pull code from GitHub
                checkout scm
            }
        }
        stage('Verify') {
            steps {
                script {
                    if (fileExists('index.html')) {
                        echo "index.html found, proceeding..."
                    } else {
                        error "index.html not found!"
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
                // Example: copy to Jenkins workspace output folder
                sh '''
                mkdir -p ${WORKSPACE}/deploy
                cp index.html ${WORKSPACE}/deploy/
                echo "index.html deployed to ${WORKSPACE}/deploy/"
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
