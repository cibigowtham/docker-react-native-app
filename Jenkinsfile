pipeline {
  agent any
  stages {
    stage('Prepare') {
      steps {
        echo 'listing all the files'
        sh 'ls -l'
        CURR_PS = sh(
          script: "cat docker-ps.txt | grep 'navis/smartaccess-api-gateway-builder' | grep -o '^[a-z0-9A-Z]\\+'",
          returnStdout: true
        )
        echo "Current running processes ${CURR_PS}"
      }
    }
  }
}
