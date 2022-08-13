pipeline {
    agent any 
    stages {
        stage('Install') {
            steps {
                sh 'pwd'
                sh 'npm install'
            }
        }
        stage('Build') {
            steps {
                sh 'pwd'
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
