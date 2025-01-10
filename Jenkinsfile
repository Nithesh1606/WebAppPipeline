pipeline {
    agent any
    environment {
        PATH = "/usr/bin/npm:${env.PATH}"
    }
    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/Nithesh1606/WebAppPipeline.git'
            }
        }
        stage('Install Dependencies') {
            steps {
                sh 'npm install -g htmlhint'
            }
        }
        stage('Run HTMLLint') {
            steps {
                sh 'htmlhint index.html'
            }
        }
        stage('Deploy to Server') {
            steps {
                sh '''
                # Assuming you're deploying to a server directory
                WEB_SERVER_DIR=/var/www/html/web-app
                mkdir -p $WEB_SERVER_DIR
                cp -r * $WEB_SERVER_DIR
                '''
            }
        }
    }
}

