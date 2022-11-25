pipeline {
    agent any
    environment {
        OLD_PROCESSES = ''
    }
    stages {
        stage('Prepare') {
            steps {
                script {
                    try {
                        OLD_PROCESSES = sh(
                                script: "cat docker-ps.txt | grep 'navis/smartaccess-api-gateway-builder' | grep -o '^[a-z0-9A-Z]\\+'",
                                returnStdout: true
                        ).trim().replaceAll('\\n', ' ')
                    } catch (e){
                        OLD_PROCESSES = ''
                    }
                    echo "Old running processes ${OLD_PROCESSES}"
                }
                when {
                    expression { OLD_PROCESSES != '' }
                }
                echo "Stopping old processes"
                echo "docker kill ${OLD_PROCESSES}"
            }
        }
    }
}
