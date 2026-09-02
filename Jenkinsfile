pipeline {
    agent any

    stages {

        stage('Build') {
            steps {
                echo 'Building the project...'
                bat 'echo Build successful > build-output.txt'
            }
        }

        stage('Test') {
            steps {
                echo 'Testing the project...'
                bat 'if not exist build-output.txt exit /b 1'
                echo 'Test passed successfully!'
            }
        }

        stage('Archive') {
            steps {
                archiveArtifacts artifacts: 'build-output.txt',
                    fingerprint: true
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully!'
        }
        failure {
            echo 'Pipeline failed!'
        }
    }
}
