pipeline {
  agent any
  stages {
    stage('checkout') {
      steps {
        git(url: 'https://github.com/m20am/cucumberbasic.git', branch: 'master', credentialsId: '72fbeef1-bd69-4916-98d1-f3d9717646ac')
      }
    }
    stage('DB2 jar and Yarn') {
      parallel {
        stage('install db2 jar') {
          steps {
            dir(path: 'core/src/main/java/com/sadad/sw/core/lib') {
              sh 'scripts.sh'
            }

          }
        }
        stage('run yarn') {
          steps {
            dir(path: 'manager/src/main/webapp') {
              sh 'git config --global url."https://github.com".insteadOf git://github.com'
              sh 'yarn'
              sh 'npm run build-rtl'
            }

          }
        }
      }
    }
    stage('build') {
      steps {
        sh 'mvn clean install -P prod -DskipTests'
      }
    }
    stage('test') {
      steps {
        sh 'mvn test'
        junit 'target/surefire-reports/*.xml'
      }
    }
    stage('send manager file') {
      parallel {
        stage('send manager file') {
          steps {
            sh 'cp ./packages/manager/*.jar  /opt/rahsam/manager'
            sh 'cd /opt/rahsam/manager'
            sh 'chmod +x manager.jar'
            sh 'SPRING_PROFILES_ACTIVE=prod'
            sh 'service rahmanager restart'
          }
        }
        stage('send worker file') {
          steps {
            sh 'cp ./packages/worker/*.jar /opt/rahsam/worker'
            sh 'cd /opt/rahsam/worker'
            sh 'chmod +x worker.jar'
            sh 'SPRING_PROFILES_ACTIVE=prod'
            sh 'service rahworker restart'
          }
        }
      }
    }
  }
  environment {
    NODE_TLS_REJECT_UNAUTHORIZED = '0'
  }
}