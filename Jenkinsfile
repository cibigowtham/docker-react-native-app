def OLD_PROCESSES = ''

pipeline {
    agent any
    stages {
        stage('Prepare') {
            steps {
                script {
                    OLD_PROCESSES = sh(
                            script: "cat docker-ps.txt | grep 'navis/smartaccess-api-gateway-builder' | grep -o '^[a-z0-9A-Z]\\+'",
                            returnStdout: true
                    ).trim().replaceAll('\\n', ' ')
                    echo "Old running processes ${OLD_PROCESSES}"
                }
            }
        }

        stage('Clean up'){
            when {
                environment name: 'OLD_PROCESSES', value: ''
            }
            steps {
                echo "Stopping old processes"
                echo "docker kill ${OLD_PROCESSES}"
            }
        }
    }
}
