pipeline {
    agent any

    stages {
        stage('Install dependencies') {
            steps {
                sh 'pip install -r requirements.txt'
            }
        }

        stage('Run unit tests') {
            steps {
                sh 'pytest -q --junitxml=pytest-report.xml'
            }
            post {
                always {
                    junit 'pytest-report.xml'
                }
            }
        }

        stage('Package') {
            steps {
                sh 'tar -czf artifact.tar.gz *.py'
                archiveArtifacts artifacts: 'artifact.tar.gz', fingerprint: true
            }
        }

        stage('Deploy (stub)') {
            steps {
                echo '🚀 Here you would call a deploy script'
            }
        }
    }
}
