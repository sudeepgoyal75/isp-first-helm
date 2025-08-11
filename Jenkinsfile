pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building golden image'
            }
        }
        stage('Tests in Parallel') {
            parallel {
                stage('tb1') {
                    steps {
                        echo 'Running tb1...'
                    }
                }
                stage('tb2') {
                    steps {
                        echo 'Running tb2...'
                    }
                }
            }
        }
        stage('docs') {
            steps {
                echo 'Deploying..ss'
            }
        }
    }
}

