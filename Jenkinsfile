pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Parallel Checks') {
            parallel {
                stage('Frontend Check') {
                    steps {
                        echo 'Starting frontend checks...'
                        // Changed 'sh' to 'bat' for Windows, and fixed the file name
                        bat 'python front.py' 
                    }
                }
                stage('Backend Check') {
                    steps {
                        echo 'Starting backend checks...'
                        // Changed 'sh' to 'bat' for Windows, and fixed the file name
                        bat 'python back.py'
                    }
                }
            }
        }

        stage('Archive Reports') {
            steps {
                echo 'Archiving generated reports...'
                archiveArtifacts artifacts: '*_report.txt', allowEmptyArchive: false
            }
        }
    }
}
