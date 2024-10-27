pipeline {
    agent any

    stages {
        stage('Print Branch Name') {
            steps {
                script {
                    echo "Branch name from env.BRANCH_NAME: ${env.BRANCH_NAME}"
                }
            }
        }
    }
}
