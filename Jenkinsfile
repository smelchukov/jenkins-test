def agentLabel
if (BRANCH_NAME == "master") {
    agentLabel = "test-prod"
} else {
    agentLabel = "prod"
}

pipeline {
    
    environment {
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
                echo BRANCH_NAME
            }
        }
        stage('Prod Deploy') {
            when {
                branch 'master'
            }
            environment {
                FOO='inner'
                SECRET = credentials('secret')
            }
            steps {
                sh 'docker-compose up -d'
            }
        }
    }
}
