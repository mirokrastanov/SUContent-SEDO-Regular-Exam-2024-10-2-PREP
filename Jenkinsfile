pipeline {
    agent any

     stages {
        stage('Get Branch Name') {
            steps {
                script {
                    env.ACTUAL_BRANCH = sh(
                        script: "git symbolic-ref --short HEAD || git rev-parse --short HEAD",
                        returnStdout: true
                    ).trim()
                    echo "Branch detected: ${env.ACTUAL_BRANCH}"
                }
            }
        }
    
    stages {
        stage('Restore dependencies') {
            when {
                branch 'feature-ci-pipeline'
            }
            steps {
                bat 'dotnet restore'
            }
        }
        stage('Build project') {
            when {
                branch 'feature-ci-pipeline'
            }
            steps {
                bat 'dotnet build --no-restore'
            }
        }
        stage('Execute tests') {
            when {
                branch 'feature-ci-pipeline'
            }
            steps {
                bat 'dotnet test --no-build --verbosity normal'
            }
        }
    }
}
