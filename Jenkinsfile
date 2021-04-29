pipeline {
    agent any

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
            
            // steps {
            //     sh 'dotnet test'
            // }
        }

        // stage('DotNet Test') {
        //     steps {
        //         sh 'pwd && dotnet test'
        //     }
        // }

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
            // NPM Tests 
            // steps {
            //     sh 'cd DotnetTemplate.Web && npm t && npm run lint'
            // }
        }

        // stage('NPM Test') {
        //     // agent {
        //     //     docker { image 'node:14-alpine' }
        //     // }
        //     steps {
        //         sh 'cd DotnetTemplate.Web && npm t && npm run lint'
        //     }
        // }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}