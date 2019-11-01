pipeline {
    agent any
    stages {
        stage('Deploy') {
            steps {
                retry(3) {
                    sh './shells/flakey-deploy.sh'
                }

                timeout(time: 3, unit: 'MINUTES') {
                    sh './shells/health-check.sh'
                }
            }
        }
    }
}