pipeline {
    agent test-prod

    stages {
        stage('Build') {
            steps {
                sh 'docker-compose build'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        stage('Stop') {
            steps {
                docker-compose down
            }
        }
        stage('Deploy') {
            steps {
                docker-compose up -d
            }
        }
    }
}
