pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/Akarunkumarthandapni09/Dotnet-MVC-Project.git'
            }
        }

        stage('Install .NET 9 SDK') {
            steps {
                bat '''
                powershell -Command "Invoke-WebRequest -Uri https://download.visualstudio.microsoft.com/download/pr/ffb5f67a-09a0-44d8-ae6d-9c9d81c2e5a4/9a6cc7984b52eec60a3b5f5b62bfb367/dotnet-sdk-9.0.100-preview-win-x64.exe -OutFile dotnet-sdk-9.exe"
                start /wait dotnet-sdk-9.exe /quiet /norestart
                dotnet --version
                '''
            }
        }

        stage('Restore') {
            steps {
                bat 'dotnet restore Event.sln'
            }
        }

        stage('Build') {
            steps {
                bat 'dotnet build Event.sln --configuration Release'
            }
        }

        stage('Test') {
            steps {
                bat 'dotnet test Event.sln --no-build --verbosity normal'
            }
        }

        stage('Publish') {
            steps {
                bat 'dotnet publish Event.sln -c Release -o publish_output'
            }
        }
    }
}
