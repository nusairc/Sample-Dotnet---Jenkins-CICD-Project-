pipeline {
    agent any

    stages {
        stage('Git Checkout') {
            steps {
                git branch: 'main', credentialsId: 'git_key', url: 'https://github.com/nusairc/lhd-helloworld.git'
            }
        }

        stage('Build') {
            steps {
                dir('./Example Hello World Apps/C#/MyApp') {
                    sh 'dotnet build'
                }
            }
        }

        stage('Unit Test') {
            steps {
                dir('./Example Hello World Apps/C#/MyApp') {
                    sh 'dotnet test'
                }
            }
        }
        

        // Add additional stages for unit tests, code analysis, etc.
    }
}
