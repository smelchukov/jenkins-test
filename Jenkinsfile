def agentLabel
if (env.BRANCH_NAME == "master") {
    agentLabel = "test-prod"
} else {
    agentLabel = "prod"
}

def getFoo(branch) {
  if (env.BRANCH_NAME == 'master') {
    return 'Foo-production'
  } else {
    return 'Foo-staging'
 }
}

pipeline {
    
    environment {
        FOO = "foo-master"
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
