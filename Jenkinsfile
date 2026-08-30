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
        stage('Push to ECR') {
            steps {
                 withCredentials([usernamePassword(
                    credentialsId: 'aws-ecr-credentials',
                    usernameVariable: 'AWS_ACCESS_KEY_ID',
                    passwordVariable: 'AWS_SECRET_ACCESS_KEY'
                )]) {
                    bat '''
                    set AWS_DEFAULT_REGION=ca-central-1
                    aws ecr get-login-password --region ca-central-1 | "C:\\Users\\afree\\AppData\\Local\\Programs\\DockerDesktop\\resources\\bin\\docker.exe" login --username AWS --password-stdin 238086621844.dkr.ecr.ca-central-1.amazonaws.com

                    "C:\\Users\\afree\\AppData\\Local\\Programs\\DockerDesktop\\resources\\bin\\docker.exe" tag devops-flask-app:latest 238086621844.dkr.ecr.ca-central-1.amazonaws.com/devops-flask-app:latest

                    "C:\\Users\\afree\\AppData\\Local\\Programs\\DockerDesktop\\resources\\bin\\docker.exe" push 238086621844.dkr.ecr.ca-central-1.amazonaws.com/devops-flask-app:latest
                    '''
                }
            }
        }
    }
}