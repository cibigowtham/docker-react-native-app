pipeline {
    agent any 
    stages {
        stage('Install') {
            steps {
                bat 'echo %CD%'
                bat 'npm install'
            }
        }
        stage('Checkstyle') {
            steps {
                bat 'npm run lint' 
            }
        }
        stage('Build') {
            steps {
                bat 'npm run build'
            }
        }
        stage('Test') {
            steps {
                bat 'runTest.bat' 
            }
        }
    }
}
