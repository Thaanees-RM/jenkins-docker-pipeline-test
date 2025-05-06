pipeline {
    agent any

    stages {
        stage('Clone') {
            steps {
                git 'git@github.com:Thaanees-RM/jenkins-docker-pipeline-test.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    dockerImage = docker.build('myapp:latest')
                }
            }
        }

        stage('Run Container') {
            steps {
                sh 'docker run -d -p 5000:5000 --name myapp myapp:latest'
            }
        }

        stage('Verify App') {
            steps {
                sh 'curl -f http://localhost:5000 || exit 1'
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully!'
        }
        failure {
            echo 'Pipeline failed!'
        }
    }
}
