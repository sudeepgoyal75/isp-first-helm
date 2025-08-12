pipeline {
    agent any
    environment {
        NEXT_STAGE = "" // will be set in S1
    }
    stages {
        stage('S1 - Decide Next Stage') {
            steps {
                script {
                    // Your logic here — could be based on parameters, files, API calls, etc.
                    def randomPick = new Random().nextInt(2) // 0 or 1

                    if (randomPick == 0) {
                        env.NEXT_STAGE = "S2"
                    } else {
                        env.NEXT_STAGE = "S3"
                    }

                    echo "S1 completed. Next stage will be: ${env.NEXT_STAGE}"
                }
            }
        }

        stage('S2 - Run if chosen') {
            when {
                expression { env.NEXT_STAGE == "S2" }
            }
            steps {
                echo "Running Stage S2"
            }
        }

        stage('S3 - Run if chosen') {
            when {
                expression { env.NEXT_STAGE == "S3" }
            }
            steps {
                echo "Running Stage S3"
            }
        }
    }
}

