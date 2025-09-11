pipeline {
    agent any

    tools {
        dotnet 'dotnet6'   
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/Akarunkumarthandapni09/Dotnet-MVC-Project.git'
            }
        }

        stage('Restore') {
            steps {
                sh 'dotnet restore Event.sln'
            }
        }

        stage('Build') {
            steps {
                sh 'dotnet build Event.sln --configuration Release'
            }
        }

        stage('Test') {
            steps {
                sh 'dotnet test Event.sln --no-build --verbosity normal'
            }
        }

        stage('Publish') {
            steps {
                sh 'dotnet publish Event.sln -c Release -o publish_output'
            }
        }
    }
}
