pipeline {
    agent none

    stages {
        stage('Checkout') {
            agent any
            steps {
                checkout scm
            }
        }

        stage('Install dependencies') {
            agent {
                docker { image 'python:3.11' }
            }
            steps {
                sh 'pip install -r requirements.txt'
            }
        }

        stage('Run tests') {
            agent {
                docker { image 'python:3.11' }
            }
            steps {
                sh 'pip install -r requirements.txt'
                sh 'pytest test_mensualite.py -v'
            }
        }

        stage('Build Docker image') {
            agent any
            steps {
                sh 'docker build -t python_jenkins_2026 .'
            }
        }
    }
}
