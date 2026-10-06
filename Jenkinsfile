```groovy
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
                    echo "===== ARCHIVOS EN JENKINS ====="
                    ls -la "$WORKSPACE"

                    echo "===== PRUEBAS EN PYTHON ====="

                    docker run --rm \
                        -v jenkins_home:/jenkins_home \
                        -w /jenkins_home/workspace/Repo_suma \
                        python:3.11-slim \
                        python -m unittest test_app.py
                '''
            }
        }
    }
}
```
