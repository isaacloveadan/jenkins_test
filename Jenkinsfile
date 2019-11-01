pipeline {
    agent any
    stages {
        stage('Deploy') {
            steps {
                retry(3) {
                    sh 'chmod a+x ./shells/flakey-deploy.sh'
                    sh './shells/flakey-deploy.sh'
                }

                timeout(time: 3, unit: 'MINUTES') {
                    sh 'chmod a+x ./shells/health-check.sh'
                    sh './shells/health-check.sh'
                }
            }
        }
    }
    post {
        always {
            echo 'This will always run'
        }
        success {
            echo 'This will run only if successful'
        }
        failure {
            echo 'This will run only if failed'
        }
        unstable {
            echo 'This will run only if the run was marked as unstable'
        }
        changed {
            echo 'This will run only if the state of the Pipeline has changed'
            echo 'For example, if the Pipeline was previously failing but is now successful'
        }
    }
}