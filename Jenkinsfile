pipeline {
  agent any
  stages {
    stage('checkout') {
      steps {
        git(url: 'https://github.com/m20am/cucumberbasic.git', branch: 'master', changelog: true, credentialsId: 'cba6c8936b5cdf9e9dae50005dfb245741b56568', poll: true)
      }
    }
  }
  environment {
    NODE_TLS_REJECT_UNAUTHORIZED = '0'
  }
}