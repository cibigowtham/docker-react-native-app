pipeline {
  agent any
  stages {
    stage('Prepare') {
      environment {
        CURR_PS = ''
      }
      steps {
        script {
          CURR_PS = sh(
            script: "cat docker-ps.txt | grep 'navis/smartaccess-api-gateway-builder' | grep -o '^[a-z0-9A-Z]\\+'",
            returnStdout: true
          ).trim().replaceAll('\\n', ' ')
          echo "Current running processes ${CURR_PS}"
        }
       when {
          environment name: 'CURR_PS', value: ''
        }
        echo 'listing all the files'
        sh 'ls -l'
      }
    }
  }
}
