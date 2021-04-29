pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                bat 'dotnet build'
                bat 'npm install'
                bat 'npm run build'
            }
        }
        stage('Test') {
            steps {
                bat 'cd DotnetTemplate.Web.Tests'
                bat 'dotnet test'
                bat 'cd DotnetTemplate.Web'
                bat 'npm t'
                bat 'npm run lint'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}