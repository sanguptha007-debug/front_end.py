pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Pulls the latest code from your configured Git repository
                checkout scm
            }
        }

        stage('Parallel Checks') {
            parallel {
                stage('Frontend Check') {
                    steps {
                        echo 'Starting frontend checks...'
                        // Uses 'bat' for Windows or 'sh' for Linux/macOS
                        sh 'python frontend_check.py' 
                    }
                }
                stage('Backend Check') {
                    steps {
                        echo 'Starting backend checks...'
                        sh 'python backend_check.py'
                    }
                }
            }
        }

        stage('Archive Reports') {
            steps {
                echo 'Archiving generated reports...'
                // Saves both text files as build artifacts in Jenkins
                archiveArtifacts artifacts: '*_report.txt', allowEmptyArchive: false
            }
        }
    }
}
