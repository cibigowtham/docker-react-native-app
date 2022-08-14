pipeline {
    agent any 
    stages {
        stage('Install') {
            steps {
                bat 'pwd'
                bat 'npm install'
            }
        }
        stage('Build') {
            steps {
                bat 'pwd'
                bat 'npm run build'
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
