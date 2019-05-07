pipeline {
  agent any
  stages {
    steps {
      script {
        withVaultCredentials([
          [path: 'secret/sweetiq/quay/sweetiq-push', keys: [username: 'QUAY_USER', password: 'QUAY_PASSWORD']]
        ]) {
          sh "docker build -t quay.io/gannett/migrate ."
          sh "docker push quay.io/gannett/migrate"
        }
      }
    }
  }
}