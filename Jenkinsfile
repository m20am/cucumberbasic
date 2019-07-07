pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        echo '${NAME}'
        NAME='Abedini Moghanaki'
        sh 'echo Building... '
        sh 'echo parameters ${EXECUTE_YARN}'
        sh 'echo parameters ${EXECUTE_TEST_CHECK}'
        sh 'echo parameters ${ONE}'
      }
    }
    stage('One') {
      when {
        expression {
          params.EXECUTE_YARN == 'Yes'
        }

      }
      steps {
        echo '${NAME}'
        echo 'Execute EXECUTE_YARN: ${EXECUTE_YARN}'
      }
    }
    stage('TWO') {
      when {
        expression {
          params.EXECUTE_TEST_CHECK == true
        }

      }
      steps {
        echo '${NAME}'
        echo 'Execute EXECUTE_TEST_CHECK: ${EXECUTE_TEST_CHECK}'
      }
    }
    stage('Three') {
      when {
        expression {
          params.ONE == false
        }

      }
      steps {
        echo 'Execute ONE: ${ONE}'
      }
    }
  }
  environment {
    NAME = 'MAJID'
  }
  parameters {
    booleanParam(defaultValue: true, description: 'Do you wanna execute tests?', name: 'EXECUTE_TEST_CHECK')
    booleanParam(defaultValue: false, description: 'Do you wanna execute yarn command?', name: 'ONE')
    choice(choices: ['Yes', 'No'], description: 'Do you wanna execute yarn command?', name: 'EXECUTE_YARN')
  }
}
