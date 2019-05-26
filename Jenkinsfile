pipeline {
    agent test-prod

    stages {
        stage('Build') {
            steps {
                docker-compose up
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
