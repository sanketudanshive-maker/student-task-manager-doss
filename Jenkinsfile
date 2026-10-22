
pipeline {
    agent any

    triggers {
        pollSCM('H/2 * * * *')
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Verify Project Files') {
            steps {
                bat 'if not exist index.html exit /b 1'
                bat 'if not exist style.css exit /b 1'
                bat 'if not exist script.js exit /b 1'

                echo 'All required project files are present'
            }
        }

        stage('Build Verification') {
            steps {
                echo 'Static project verification completed'
            }
        }
    }

    post {
        success {
            echo 'CI BUILD SUCCESSFUL'
        }

        failure {
            echo 'CI BUILD FAILED - Check Console Output'
        }
    }
}
