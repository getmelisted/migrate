pipeline {
  agent any
  stages {
    stage('docker build') {
      steps {
        script {
          withVaultCredentials([
            [path: 'secret/sweetiq/quay/sweetiq-push', keys: [username: 'QUAY_USER', password: 'QUAY_PASSWORD']]
          ]) {
            sh "echo ${QUAY_PASSWORD} | docker login --password-stdin -u ${QUAY_USER} quay.io"
            sh "docker build -t quay.io/gannett/migrate ."
            sh "docker push quay.io/gannett/migrate"
          }
        }
      }
    }
  }
}