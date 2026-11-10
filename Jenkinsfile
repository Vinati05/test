pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'python3 -m venv .venv'
                sh '.venv/bin/pip install Flask pytest'
            }
        }

        stage('Run Tests') {
            steps {
                sh '.venv/bin/pytest test_app.py -v'
            }
        }
    }

    post {
        success {
            echo 'Flask application tested successfully!'
        }

        failure {
            echo 'Pipeline failed!'
        }
    }
}
