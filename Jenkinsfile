pipeline {
    agent any 
    environment {
        PROD_IMAGE_NAME = 'scibigowtham/reactweb'
        TEST_IMAGE_NAME = 'scibigowtham/reactweb-dev'
    }
    stages {
        stage('Docker Build') {
            steps {
                bat 'echo %CD%'
                bat 'echo building docker image'
                bat 'docker build -t $PROD_IMAGE_NAME .'
                bat 'echo "docker image successfully created"'
                bat 'docker build -t $TEST_IMAGE_NAME -f Dockerfile.dev .'
                bat 'echo docker dev image created'
            }
        }
        stage('Checkstyle') {
            steps {
                bat 'docker run --rm $TEST_IMAGE_NAME npm run lint' 
            }
        }
        stage('Test') {
            steps {
                bat 'docker run --rm -e CI=true $TEST_IMAGE_NAME npm run test -- --coverage' 
                bat 'echo tests ran successfully'
            }
        }
        stage('Docker Push & Clean Up') {
            steps {
                bat 'docker push $PROD_IMAGE_NAME'
                bat 'echo image pushed to docker hub'
                bat 'docker rmi $TEST_IMAGE_NAME'
                bat 'echo cleaned up docker containers and images'
            }
        }
    }
}
