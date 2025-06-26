pipeline {
    agent any

    stages {
        stage('CI pipeline – allowed branches') {
            when {
                anyOf {
                    branch 'feature/.+'
                    branch 'main'
                }
            }

            stages {
                stage('Checkout') {
                    steps {
                        checkout scm
                    }
                }

                stage('Restore Dependencies') {
                    steps {
                        bat 'dotnet restore'
                    }
                }

                stage('Build App') {
                    steps {
                        bat 'dotnet build --no-restore'
                    }
                }

                stage('Execute All Tests') {
                    steps {
                        bat 'dotnet test --no-build --verbosity normal'
                    }
                }
            }
        }
    }
}
