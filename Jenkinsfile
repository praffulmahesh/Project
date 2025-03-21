pipeline {
    agent any

    environment {
        // Define any environment variables here
        MY_ENV_VAR = 'value'
    }

    stages {
        stage('Checkout') {
            steps {
                // Checkout source code from a repository
                git url: 'https://github.com/praffulmahesh/Project.git', branch: 'main'
            }
        }

        stage('Build') {
            steps {
                // echo 'Building the application...'
                sh '''
                #!/usr/local/bin
                echo "Running build commands..."
                # Example build command (replace with your actual command)
                npm install
                npm run build
                '''
            }
        }

        stage('Test') {
            steps {
                // echo 'Running tests...'
                sh '''
                #!/bin/bash
                echo "Running test commands..."
                # Example test command (replace with your actual command)
                npm test
                '''
            }
        }

        stage('Deploy') {
            steps {
                // echo 'Deploying the application...'
                sh '''
                #!/bin/bash
                echo "Running deployment commands..."
                # Example deployment command (replace with your actual command)
                scp -r build/ user@server:/path/to/deploy
                ssh user@server 'systemctl restart my-app'
                '''
            }
        }
    }

    post {
        success {
            echo 'Pipeline succeeded!'
        }
        failure {
            echo 'Pipeline failed.'
        }
        always {
            echo 'Cleaning up...'
            cleanWs() // Cleans up the workspace
        }
    }
}
