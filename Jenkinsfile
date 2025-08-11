pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/username/my-repo.git'
            }
        }
        stage('Build') {
            steps {
                echo 'Building...'
                sh 'echo "Build step here"'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing...'
                sh 'echo "Run tests here"'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying...'
                sh 'echo "Deploy step here"'
            }
        }
    }
}
