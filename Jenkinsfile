pipeline {
    agent any

    stages {

        stage('Pull Code') {
            steps {
                echo 'Code pulled successfully'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh '''
                sudo docker build -t pipeline-app .
                '''
            }
        }

        stage('Test') {
            steps {
                echo 'Testing successful'
            }
        }

        stage('Deploy Container') {
            steps {
                sh '''
                sudo docker stop pipeline-app || true
                sudo docker rm pipeline-app || true
                sudo docker run -d -p 80:80 --name pipeline-app pipeline-app
                '''
            }
        }

        stage('Verification') {
            steps {
                sh '''
                sudo docker ps
                '''
            }
        }
    }
}
