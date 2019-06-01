pipeline {
    agent any
    parameters {
        choice choices: ['YES', 'NO'], description: 'DO you wanna execute yarn command?', name: 'EXECUTE_YARN'
        booleanParam defaultValue: false, description: 'DO you wanna execute yarn command?', name: 'YARN_EXECUTE_CHECK'
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
