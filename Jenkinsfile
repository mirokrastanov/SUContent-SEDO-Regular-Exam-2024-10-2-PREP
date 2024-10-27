pipeline {
    agent any

    stages {
        stage('Set Branch Name') {
            steps {
                script {
                    // Fetch branch name using Git and set it to an environment variable
                    env.ACTUAL_BRANCH = sh(
                        script: 'git rev-parse --abbrev-ref HEAD',
                        returnStdout: true
                    ).trim()
                    echo "Detected branch: ${env.ACTUAL_BRANCH}"
                }
            }
        }
        
        stage('Restore dependencies') {
            when {
                expression { env.ACTUAL_BRANCH == 'feature-ci-pipeline' }
            }
            steps {
                bat 'dotnet restore'
            }
        }
        stage('Build project') {
            when {
                expression { env.ACTUAL_BRANCH == 'feature-ci-pipeline' }
            }
            steps {
                bat 'dotnet build --no-restore'
            }
        }
        stage('Execute tests') {
            when {
                expression { env.ACTUAL_BRANCH == 'feature-ci-pipeline' }
            }
            steps {
                bat 'dotnet test --no-build --verbosity normal'
            }
        }
    }
}
