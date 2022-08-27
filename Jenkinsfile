pipeline{
    agent any
    environment{
        AUTHOR_NAME="James"
        GONSTEADY_PEM = credentials("gonsteady_pem")
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
                 echo "This is the running stage";
                 sh 'ssh -T -i $GONSTEADY_PEM ubuntu@ec2-18-134-182-112.eu-west-2.compute.amazonaws.com'
                 sh "sudo rm -rf /var/www/html"
                 sh "sudo git -C /var/www/html pull"
            }
        }

        stage("production"){
            steps{
                 echo "This is the production stage"
            }
        }
    }
}