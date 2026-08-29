pipeline {
    agent any

    stages {

        stage('Setup') {
            steps {
                bat 'python -m venv .venv'
                bat '.venv\\Scripts\\python -m pip install -r requirements.txt'
            }
        }

        stage('Test') {
            steps {
                bat '.venv\\Scripts\\python --version'
                bat '.venv\\Scripts\\python -c "import flask; print(\'Flask installed successfully\')"'
            }
        }

        stage('Docker Build') {
            steps {
                bat 'docker build -t devops-flask-app .'
            }
        }
    }
}