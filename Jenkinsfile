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
}