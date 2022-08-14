pipeline {
    agent any 
    stages {
        stage('Install') {
            steps {
                bash 'pwd'
                bash 'npm install'
            }
        }
        stage('Build') {
            steps {
                bash 'pwd'
                bash 'npm run build'
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
