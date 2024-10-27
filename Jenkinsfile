pipeline {
    agent any

    stages {
        stage('Checkout Branch') {
            steps {
                // Explicitly checkout the current branch
                checkout scm
            }
        }
        
        stage('Get Branch Name') {
            steps {
                script {
                    // Use Git to retrieve the branch name on Windows
                    def branchName = bat(
                        script: 'git rev-parse --abbrev-ref HEAD',
                        returnStdout: true
                    ).trim()
                    echo "Detected branch: ${branchName}"
                }
            }
        }
    }
}
