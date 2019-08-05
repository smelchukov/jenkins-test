pipeline {
    
    agent { label 'jenkins' }

    stages {
        stage('Build') {
            steps {
                sh 'echo build'
            }
        }

        stage('Test') {
            steps {
                echo 'Testing'
            }
        }
        
        stage('Deploy') {
            steps {
                sh 'echo deploy'
            }
        }

    }
}
