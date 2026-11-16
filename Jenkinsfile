
pipeline {
    agent any

    environment {
        DEPLOY_DIR = 'C:/inetpub/wwwroot'
    }

    stages {

        stage('Checkout') {
            steps {
                echo 'Downloading project from GitHub'
                git branch: 'main',
                    url: 'https://github.com/kanishka9875/Jenkins-CICD-Practical.git'
            }
        }

        stage('Build') {
            steps {
                echo 'Building the web application'
                bat 'dir'
            }
        }

        stage('Test') {
            steps {
                echo 'Testing HTML file'
                bat 'bat '"C:/Users/Ka/tidy.exe" -q -e index.html'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying website to IIS'

                bat 'if not exist "%DEPLOY_DIR%" mkdir "%DEPLOY_DIR%"'

                bat 'xcopy /Y /I index.html style.css script.js "%DEPLOY_DIR%\\"'
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully!'
            echo 'Visit http://localhost'
        }

        failure {
            echo 'Pipeline failed. Check console output.'
        }
    }
}
