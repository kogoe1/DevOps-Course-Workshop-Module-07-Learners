pipeline {
    agent none

    environment {
        DOTNET_CLI_HOME = "/tmp/DOTNET_CLI_HOME"
    }

    stages {
        stage(' DotNet Build') {
            agent {
                docker { image 'mcr.microsoft.com/dotnet/sdk:5.0' }
            }
            steps {
                sh 'dotnet build'
            }
        }

        stage('NPM Build') {
            agent {
                docker { image 'node:14-alpine' }
            }
            steps {
                sh 'npm install'
                sh 'npm run build'
            }
        }
        stage('DotNet Test') {
            steps {
                sh 'dotnet test'
            }
        }

        stage('NPM Test') {
            steps {
                sh 'cd DotnetTemplate.Web && npm t && npm run lint'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}