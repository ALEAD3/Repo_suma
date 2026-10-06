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
                    echo "===== HOST WORKSPACE ====="
                    ls -la "$WORKSPACE"

                    echo "===== CONTENEDOR PYTHON ====="
                    docker run --rm \
                    -v "$WORKSPACE:/app:Z" \
                    -w /app \
                    python:3.11-slim \
                    sh -c 'pwd; echo "---"; ls -la /app; echo "---"; python -c "import os; print(os.listdir(\\"/app\\"))"'
                '''
            }
        }
    }
}
