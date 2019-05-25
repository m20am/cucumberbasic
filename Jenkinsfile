pipeline {
  agent any
  stages {
    stage('checkout') {
      steps {
        git(url: 'https://github.com/m20am/cucumberbasic.git', branch: 'master', changelog: true, poll: true, credentialsId: '72fbeef1-bd69-4916-98d1-f3d9717646ac')
      }
    }
    stage('build') {
      steps {
        dir(path: 'core/src/main/java/com/sadad/sw/core/lib/') {
          sh 'scripts.sh'
        }
        dir(path: 'manager/src/main/webapp/') {
            sh 'git config --global url."https://github.com".insteadOf git://github.com'
            sh 'yarn'
            sh 'npm run build-rtl'
        }

      }
    }
  }
  environment {
    NODE_TLS_REJECT_UNAUTHORIZED = '0'
  }
}
