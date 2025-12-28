pipeline {
    agent { label 'docker-agent' }

    environment {
        IMAGE_NAME = "devops-demo"
        CONTAINER_NAME = "devops-demo-container"
    }

    stages {

        stage('Checkout Code') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/Rajat972/devops-project.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh '''
                docker build -t $IMAGE_NAME .
                '''
            }
        }

        stage('Run Docker Container') {
            steps {
                sh '''
                docker rm -f $CONTAINER_NAME || true
                docker run -d -p 8081:5000 --name $CONTAINER_NAME $IMAGE_NAME
                '''
            }
        }
    }

    post {
        success {
            echo "✅ Application deployed successfully"
        }
        failure {
            echo "❌ Pipeline failed"
        }
    }
}
