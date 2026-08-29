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
                bat '.venv\\Scripts\\python -m pytest'
            }
        }

        stage('Docker Build') {
            steps {
                bat '"C:\\Users\\afree\\AppData\\Local\\Programs\\DockerDesktop\\resources\\bin\\docker.exe" build -t devops-flask-app .'
            }
        }
    }
}