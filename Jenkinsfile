pipeline{
    agent any
    environment{
        NEW_VERSION='1.3.0'
    }
    stages{
        stage("compile"){
            steps{
                script{
                    echo "Compiling the code"
                }
            }
        }
        stage("test"){
            steps{
                script{
                    echo "Testing the code"
                }
            }
             post{
            always{
                echo "Testing is completed"
            }
        }
        }
       
        stage("package"){
            steps{
                script{
                    echo "Packaging the code ${NEW_VERSION}"
                }
            }
        }
    }
}