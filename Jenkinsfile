pipeline {
    agent any

    stages {
        stage('Checkout') {
            when {
                anyOf {
                    branch 'feature/**'
                    branch 'main'
                }
            }
            steps {
                checkout scm
            }
        }

        stage('Restore Dependencies') {
            when {
                anyOf {
                    branch 'feature/**'
                    branch 'main'
                }
            }
            steps {
                bat 'dotnet restore'
            }
        }

        stage('Build App') {
            when {
                anyOf {
                    branch 'feature/**'
                    branch 'main'
                }
            }
            steps {
                bat 'dotnet build --no-restore'
            }
        }

        stage('Execute All Tests') {
            when {
                anyOf {
                    branch 'feature/**'
                    branch 'main'
                }
            }
            steps {
                bat 'dotnet test --no-build --verbosity normal'
            }
        }
    }
}
