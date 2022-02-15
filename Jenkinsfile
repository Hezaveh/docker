pipeline {
    environment {
        registry = '044545860366.dkr.ecr.us-east-1.amazonaws.com/my-app'
        registryCredential = 'aws-credentials'
        dockerImage = ''
    }
    agent any
    stages {
        stage('Building image') {
            steps{
                script {
                    dockerImage = docker.build registry + ":1.6"
                }
            }
        }
        stage('Deploy image') {
            steps{
                script{
                    docker.withRegistry("https://" + registry, "ecr:us-east-1:" + registryCredential) {
                        dockerImage.push()
                    }
                }
            }
        }
        stage('Build') {
            steps {
                echo 'Building..'
                withAWS(credentials: 'aws-credentials', region: 'us-east-1') {
                    echo 'hi'
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