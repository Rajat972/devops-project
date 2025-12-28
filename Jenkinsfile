pipeline {
    agent any

    stages {
        stage('Clone Repo') {
            steps {
                git 'https://github.com/<your-username>/devops-project.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t devops-demo .'
            }
        }

        stage('Run Container') {
            steps {
                sh '''
                docker rm -f devops-demo || true
                docker run -d -p 8081:5000 --name devops-demo devops-demo
                '''
            }
        }
    }
}
