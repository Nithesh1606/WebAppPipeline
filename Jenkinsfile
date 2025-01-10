pipeline {
    agent any
    stages {
        stage('Checkout Code') {
            steps {
                echo "Cloning the Git repository..."
                git branch: 'main', url: 'https://github.com/your-username/web-app.git'
            }
        }
        stage('Code Quality Check') {
            steps {
                echo "Running code quality checks..."
                sh '''
                npm install -g htmlhint || true
                htmlhint index.html
                '''
            }
        }
        stage('Archive Artifacts') {
            steps {
                echo "Archiving web application artifacts..."
                archiveArtifacts artifacts: '**/*', fingerprint: true
            }
        }
        stage('Deploy to Web Server') {
            steps {
                echo "Deploying to web server..."
                sh '''
                WEB_SERVER_DIR=/var/www/html/web-app
                mkdir -p $WEB_SERVER_DIR
                cp -r * $WEB_SERVER_DIR
                '''
            }
        }
    }
}

