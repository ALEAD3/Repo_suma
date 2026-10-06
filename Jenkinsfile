pipeline {
    agent any

    stages {
        stage('Clonar Código') {
            steps {
                checkout scm
            }
        }

        stage('Ejecutar Pruebas Python') {
            steps {
                sh '''
                    docker run --rm \
                    -v "$WORKSPACE:/app" \
                    -w /app \
                    python:3.11-slim \
                    python -m unittest test_app.py
                '''
            }
        }
    }
}
