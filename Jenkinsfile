pipeline {
    /*  Runs on any agent the master can reach.
        For repeatability we’ll spin up a Python Docker container
        so builds are identical everywhere.                         */
    agent {
        docker {
            image 'python:3.11-slim'
            args  '-u root'          // allows pip to write to cache
        }
    }

    stages {

        stage('Install dependencies') {
            steps {
                sh 'pip install --quiet -r requirements.txt'
            }
        }

        stage('Run unit tests') {
            steps {
                // -q keeps pytest output tidy
                sh 'pytest -q --junitxml=pytest-report.xml'
            }
            /*  Tell Jenkins where test results live so they show up
                in the UI.  */
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
                echo '🚀  Here you would call a deploy script or helm chart'
            }
        }
    }
}
