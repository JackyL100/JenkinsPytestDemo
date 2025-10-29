pipeline {
    agent {
        docker { image 'python:3.10-slim' }
    }
    stages {
        stage('Install dependencies') {
            steps {
                sh 'python3 -m venv venv'
                sh './venv/bin/pip install -r requirements.txt'
            }
        }   
        stage('Run tests') {
            steps {
                sh './venv/bin/pytest --junitxml=report.xml'
                }
        }
        stage('Publish Report') {
            steps {
                junit 'report.xml'
            }
        }
    }
}