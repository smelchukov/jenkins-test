def branchName = getCurrentBranch()
echo 'My branch is' + branchName

def agentLabel
if (branchName == "master") {
    agentLabel = "test-prod"
} else {
    agentLabel = "prod"
}

def getCurrentBranch () {
    return sh (
        script: 'git rev-parse --abbrev-ref HEAD',
        returnStdout: true
    ).trim()
}

def getFoo() {
  if (branchName == 'master') {
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
