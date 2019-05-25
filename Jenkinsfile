pipeline {
  agent any
  stages {
    stage('checkout') {
      steps {
        git(url: 'https://github.com/m20am/cucumberbasic.git', branch: 'master', changelog: true, poll: true, credentialsId: '72fbeef1-bd69-4916-98d1-f3d9717646ac')
      }
    }
  }
  environment {
    NODE_TLS_REJECT_UNAUTHORIZED = '0'
  }
}