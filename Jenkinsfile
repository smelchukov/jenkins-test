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
                echo 'Testing 2'
            }
        }
        
        stage('Deploy') {
            steps {
                sh 'echo deploy'
            }
        }
    }
}
