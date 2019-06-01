pipeline {
    agent any
    parameters {
        choice choices: ['Yes', 'No'], description: 'Do you wanna execute yarn command?', name: 'EXECUTE_YARN'
    }
    stages {
        stage('Build') {
            steps {
                sh 'echo Building... '
                sh 'echo parameters ${EXECUTE_YARN}'
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
