pipeline {
    agent none

    environment {
        DOTNET_CLI_HOME = "/tmp/DOTNET_CLI_HOME"
    }

    stages {
        stage(' DotNet Build and Test') {
            agent {
                docker { 
                    image 'mcr.microsoft.com/dotnet/sdk:5.0'
                    reuseNode true 
                }
            }
            steps {
                sh 'dotnet build && dotnet test'
            }
        
        }

        stage('NPM Build and Tests') {
            agent {
                docker { 
                    image 'node:14-alpine' 
                    reuseNode true
                }
            }
            steps {
                sh 'cd DotnetTemplate.Web && npm init -y && npm install && npm run build && npm t && npm run lint'
            }
            
        }

        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}