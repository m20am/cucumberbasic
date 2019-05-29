pipeline {

    agent any

    stages {
        stage ('Build') {
            steps {
                sh 'echo Building... '
            }
        }
        
        stage ('Test') {
            steps {
                script {
                    try {
                        echo 'Running tests...'
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
