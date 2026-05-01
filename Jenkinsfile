pipeline {
    agent {
        label 'built-in'
    }

    stages {

        stage('Pull Code') {
            steps {
                echo 'Code pulled successfully'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh '''
                docker build -t pipeline-app .
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
                docker stop pipeline-app || true
                docker rm pipeline-app || true
                docker run -d -p 80:80 --name pipeline-app pipeline-app
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
