pipeline{
    agent any
    environment{
        AUTHOR_NAME="James"
    }
    parameters{
        choice(name: "VERSION", choices: ["1.1.0", "1.1.1"])
    }
    stages{
        stage("testing"){
            when{
                expression{
                    BRANCH_NAME == 'testing'
                }
            }
            steps{
                echo "This is the testing stage ${env.AUTHOR_NAME}"
            }
        }

        stage("running"){
            steps{
                 echo "This is the running stage"
            }
        }

        stage("production"){
            steps{
                 echo "This is the production stage"
            }
        }
    }
}