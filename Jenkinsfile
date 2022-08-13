pipeline {
    agent any 
    stages {
        stage('Build') {
            steps {
                echo 'npm run build' 
            }
        }
        stage('Checkstyle') {
            steps {
                echo 'npm lint' 
            }
        }
        stage('Test') {
            steps {
                echo 'npm run test' 
            }
        }
    }
}