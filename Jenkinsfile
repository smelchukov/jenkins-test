def agentLabel
if (BRANCH_NAME == "master") {
    agentLabel = "test-prod"
} else {
    agentLabel = "prod"
}

def getFoo() {
  if (BRANCH_NAME == 'master') {
    return 'Foo-production'
  } else {
    return 'Foo-staging'
 }
}

pipeline {
    
    environment {
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
                echo env.BRANCH_NAME
            }
        }
        stage('Deploy') {
            steps {
                sh 'docker-compose up -d'
            }
        }
    }
}
