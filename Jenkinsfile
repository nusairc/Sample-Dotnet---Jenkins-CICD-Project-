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

        stage('Code Analysis') {
            steps {
                withSonarQubeEnv('SonarCloud') {
                    // Run SonarCloud analysis
                    sh 'dotnet sonarscanner begin /k:"nusairc_lhd-helloworld" /d:sonar.login="3197b75fc357e4836d96cf32e9a21610e89a79ec"'
                    sh 'dotnet build'
                    sh 'dotnet sonarscanner end /d:sonar.login="3197b75fc357e4836d96cf32e9a21610e89a79ec"'
                }
            }
        }
        

        // Add additional stages for unit tests, code analysis, etc.
    }
}
