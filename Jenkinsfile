pipeline {
    environment {
        FOO = "foo"
        SECRET = credentials('secret')
    }
    
    agent { label 'test-prod' }

    stages {
        stage('Build') {
            steps {
                sh 'docker-compose build'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..2'
            }
        }
        stage('Deploy') {
            steps {
                sh 'docker-compose up -d'
            }
        }
    }
}
