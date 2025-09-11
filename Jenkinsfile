pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/Akarunkumarthandapni09/Dotnet-MVC-Project.git'
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
