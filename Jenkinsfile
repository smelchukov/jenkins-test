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
                sh 'docker-compose down'
            }
        }
        stage('Deploy') {
            steps {
                sh 'docker-compose up -d'
            }
        }
    }
}
