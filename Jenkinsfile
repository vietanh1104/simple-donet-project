pipeline {
    agent any

    environment {
        IMAGE_NAME = "simple-donet-project"
        TAG = "latest"
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/vietanh1104/simple-donet-project.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh "docker build -t ${IMAGE_NAME}:${TAG} ."
            }
        }

        stage('Run Container') {
            steps {
                sh "docker rm -f myapp || true"
                sh "docker run -d --name myapp -p 8081:80 ${IMAGE_NAME}:${TAG}"
            }
        }
    }
}
