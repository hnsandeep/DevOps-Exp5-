pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo 'Building project...'
                sh 'echo Hello World > output.txt'
            }
        }
        stage('Test') {
            steps {
                echo 'Running tests...'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying project...'
            }
        }
    }
}
