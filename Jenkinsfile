pipeline {
    agent any
    parameters {
        choice choices: ['Yes', 'No'], description: 'Do you wanna execute yarn command?', name: 'EXECUTE_YARN'
        booleanParam defaultValue: true, description: 'Do you wanna execute tests?', name: 'EXECUTE_TEST_CHECK'
        booleanParam defaultValue: false, description: 'Do you wanna execute yarn command?', name: 'ONE'
    }
    stages {
        stage('Build') {
            steps {
                sh 'echo Building... '
                sh 'echo parameters ${EXECUTE_YARN}'
                sh 'echo parameters ${EXECUTE_TEST_CHECK}'
                sh 'echo parameters ${ONE}'
            }
        }
        stage('One') {
            when {
                expression { params.EXECUTE_YARN == 'Yes' }
            }
            steps {
                echo 'Execute EXECUTE_YARN: ${EXECUTE_YARN}'
            }
        }
        stage('TWO') {
            when {
                expression { params.EXECUTE_TEST_CHECK == true }
            }
            steps {
                echo 'Execute EXECUTE_TEST_CHECK: ${EXECUTE_TEST_CHECK}'
            }
        }
        stage('Three') {
            when {
                expression { params.ONE == false }
            }
            steps {
                echo 'Execute ONE: ${ONE}'
            }
        }
    }
}
