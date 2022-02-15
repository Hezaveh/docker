pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building..'
                sh 'aws ecr get-login-password --region us-east-1 | docker login --username AWS --password-stdin 044545860366.dkr.ecr.us-east-1.amazonaws.com'
                sh 'docker build -t my-app .'
                sh 'docker tag my-app:latest 044545860366.dkr.ecr.us-east-1.amazonaws.com/my-app:latest'
                sh 'docker push 044545860366.dkr.ecr.us-east-1.amazonaws.com/my-app:latest'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}