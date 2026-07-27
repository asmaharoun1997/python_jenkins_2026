pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Install dependencies') {
            steps {
                sh 'pip install -r requirements.txt'
            }
        }

        stage('Run tests') {
            steps {
                sh 'pytest test_mensualite.py -v'
            }
        }

        stage('Build Docker image') {
            steps {
                sh 'docker build -t python_jenkins_2026 .'
            }
        }
    }
}
