pipeline{
    agent any
    parameters{
        string(name: 'VERSION',defaultValue:"",description: 'version to deploy')
        choice(name: 'VERSION',choices:['1.1.0','1.2.0','1.3.0'])
        booleanParam(name:'executeTests',defaultvalue: true,description: "Testcases")
    }
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
            when{
                expression{
                    params.executeTests
                }
            }
            steps{
                script{
                    echo "Packaging the code ${NEW_VERSION}"
                }
            }
        }
    }
}