pipeline {
    agent any 
    stages {
        stage('Docker Build') {
            steps {
                bat 'echo %CD%'
                bat 'echo building docker image'
                bat 'docker build -t scibigowtham/reactweb .'
                bat 'echo "docker image successfully created"'
                bat 'docker build -t scibigowtham/reactweb-dev -f Dockerfile.dev .'
                bat 'echo docker dev image created'
            }
        }
        stage('Checkstyle') {
            steps {
                bat 'docker run --rm learndocker/reactweb-dev npm run lint' 
            }
        }
        stage('Test') {
            steps {
                bat 'docker run --rm -e CI=true learndocker/reactweb-dev npm run test -- --coverage' 
                bat 'echo tests ran successfully'
            }
        }
        stage('Docker Push & Clean Up') {
            steps {
                bat 'docker push scibigowtham/reactweb'
                bat 'echo image pushed to docker hub'
                bar 'docker rmi learndocker/reactweb-dev'
                bat 'echo cleaned up docker containers and images'
            }
        }
    }
}
