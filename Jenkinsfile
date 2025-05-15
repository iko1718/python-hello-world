pipeline {
    agent any

    stages {
        stage('Checkout SCM') {
            steps {
                checkout scm
            }
        }

        stage('Install dependencies') {
            steps {
                // Use 'bat' for Windows shell commands
                bat 'pip install -r requirements.txt'
            }
        }

        stage('Run unit tests') {
            steps {
                bat 'pytest'
            }
        }

        stage('Package') {
            steps {
                // Example: zip the files or do packaging steps here
                bat 'echo Packaging...'
            }
        }

        stage('Deploy (stub)') {
            steps {
                bat 'echo Deploying...'
            }
        }
    }
}
