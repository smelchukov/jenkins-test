def agentLabel
if (BRANCH_NAME == "master") {
    agentLabel = "test-prod"
} else {
    agentLabel = "prod"
}

def getFoo() {
  if (BRANCH_NAME == 'master') {
    return FOO_PROD
  } else {
    return FOO_STAGING
 }
}

pipeline {
    
    environment {
        FOO_STAGING = 's'
        FOO_PROD = 'p'
        FOO = getFoo()
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
        stage('Deploy') {
            steps {
                sh 'docker-compose up -d'
            }
        }
    }
}
