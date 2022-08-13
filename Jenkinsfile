pipeline {
    agent any 
    stages {
        stage('Build') {
            steps {
                sh 'npm run build'
            }
        }
        stage('Checkstyle') {
            steps {
                sh 'npm lint' 
            }
        }
        stage('Test') {
            steps {
                sh 'npm run test' 
            }
        }
    }
}