pipeline {
    agent any

    stages {
        stage('Clonar Código') {
            steps {
                checkout scm

                sh '''
                    echo "===== WORKSPACE ====="
                    pwd

                    echo "===== ARCHIVOS ====="
                    ls -la

                    echo "===== CONTENIDO GIT ====="
                    git status
                    git log -1 --oneline
                '''
            }
        }

        stage('Ejecutar Pruebas Python') {
            steps {
                sh '''
                    echo "===== ARCHIVOS ANTES DE DOCKER ====="
                    ls -la "$WORKSPACE"

                    docker run --rm \
                    -v "$WORKSPACE:/app:Z" \
                    -w /app \
                    python:3.11-slim \
                    python -m unittest test_app.py
                '''
            }
        }
    }
}
