pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building..'
                withAWS(credentials: 'aws-credentials', region: 'us-east-1') {
                    echo 'hi'
                    sh 'docker login --username AWS --password-stdin 044545860366.dkr.ecr.us-east-1.amazonaws.com'
                    echo 'hi2'
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