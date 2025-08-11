pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building golden image'
                sh 'mkdir -p build_output && echo "Hello from build" > build_output/result.txt'
                
                // Save files for later stages
                stash name: 'build-files', includes: 'build_output/**'
            }
        }
        stage('Tests in Parallel') {
            parallel {
                stage('tb1') {
                    steps {
                        // Retrieve build files
                        unstash 'build-files'
                        sh 'cat build_output/result.txt'
                        echo 'Running tb1...'
                    }
                }
                stage('tb2') {
                    steps {
                        unstash 'build-files'
                        sh 'cat build_output/result.txt'
                        echo 'Running tb2...'
                    }
                }
            }
        }
        stage('docs') {
            steps {
                unstash 'build-files'
                sh 'ls -l build_output'
                echo 'Deploying..ss'
            }
        }
    }
}

