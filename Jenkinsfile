
pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                echo 'Getting the source code...'
            }
        }

        stage('Build') {
            steps {
                sh 'echo "Building demo application"'
                sh 'mkdir -p build && date > build/version.txt'
            }
        }

        stage('Test') {
            steps {
                sh 'test -f build/version.txt'
                echo 'Tests passed!'
            }
        }
    }

    post {
        success {
            archiveArtifacts artifacts: 'build/*.txt'
            echo 'Pipeline succeeded!'
        }

        failure {
            echo 'Pipeline failed: check the console output'
        }

        always {
            echo 'Pipeline finished'
        }
    }
}
