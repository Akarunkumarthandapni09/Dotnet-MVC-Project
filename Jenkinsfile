pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/Akarunkumarthandapni09/Dotnet-MVC-Project.git'
            }
        }

        stage('Install .NET') {
            steps {
                sh '''
                    wget https://dot.net/v1/dotnet-install.sh -O dotnet-install.sh
                    bash dotnet-install.sh --channel 6.0 --install-dir $HOME/dotnet
                    export PATH=$HOME/dotnet:$PATH
                    dotnet --version
                '''
            }
        }

        stage('Restore') {
            steps {
                sh '$HOME/dotnet/dotnet restore Event.sln'
            }
        }

        stage('Build') {
            steps {
                sh '$HOME/dotnet/dotnet build Event.sln --configuration Release'
            }
        }

        stage('Test') {
            steps {
                sh '$HOME/dotnet/dotnet test Event.sln --no-build --verbosity normal'
            }
        }

        stage('Publish') {
            steps {
                sh '$HOME/dotnet/dotnet publish Event.sln -c Release -o publish_output'
            }
        }
    }
}
