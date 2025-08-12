pipeline {
    agent any
    stages {
        stage('S1 - Decide Next Stage') {
            steps {
                script {
                    // Decide next stage
                    def nextStage = (new Random().nextInt(2) == 0) ? "S2" : "S3"
                    // Save to currentBuild description to see in UI
                    currentBuild.description = "Next stage: ${nextStage}"
                    // Save in Jenkins environment for use in next stages
                    env.NEXT_STAGE = nextStage
                    // Also save in script binding for 'when' condition
                    binding.setVariable('nextStage', nextStage)
                    echo "S1 completed. Next stage will be: ${nextStage}"
                }
            }
        }

        stage('S2 - Run if chosen') {
            when {
                expression { 
                    // use groovy var 'nextStage' instead of env
                    return binding.hasVariable('nextStage') && binding.getVariable('nextStage') == "S2"
                }
            }
            steps {
                echo "Running Stage S2"
            }
        }

        stage('S3 - Run if chosen') {
            when {
                expression { 
                    return binding.hasVariable('nextStage') && binding.getVariable('nextStage') == "S3"
                }
            }
            steps {
                echo "Running Stage S3"
            }
        }
    }
}

