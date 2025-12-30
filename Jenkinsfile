pipeline {
    agent any

    stages {

        stage('Clone Repository') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/samibutt77/flask-jenkins-demo.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                bat '''
                python -m venv venv
                . venv/bin/activate
                pip install --upgrade pip
                pip install -r requirements.txt
                '''
            }
        }

        stage('Run Unit Tests') {
            steps {
                bat '''
                . venv/bin/activate
                pytest
                '''
            }
        }

        stage('Build Application') {
            steps {
                echo 'Build step completed (Flask app does not require compilation)'
            }
        }

        stage('Deploy Application (Simulated)') {
            steps {
                bat '''
                mkdir -p /tmp/flask-deploy
                cp -r * /tmp/flask-deploy/
                echo "Application deployed to /tmp/flask-deploy"
                '''
            }
        }
    }

    post {
        success {
            echo 'Pipeline executed successfully!'
        }
        failure {
            echo 'Pipeline failed!'
        }
    }
}
