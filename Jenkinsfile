pipeline {
  agent any
  parameters {
    choice(name: 'YARN_EXECUTE_RADIO',
            choices: 'Yes\nNo',
            description: 'Do you wanna execute yarn command?')
    booleanParam(name: 'YARN_EXECUTE_CHECK',
            defaultValue: false,
            description: 'Do you wanna execute yarn command?')
  }
  stages {
    stage('Build') {
      steps {
        sh 'echo Building... '
      }
    }
    stage('Test') {
      when {
              // Only say hello if a "greeting" is requested
          expression { params.YARN_EXECUTE_RADIO == 'YES' }
      }
      steps {
        script {
          try {
            echo 'Running tests...'
            mvn test
            sh 'exit 1'
          }
          catch (exc) {
            echo 'Testing failed!'
            currentBuild.result = 'UNSTABLE'
          }
        }

      }
    }
  }
}
