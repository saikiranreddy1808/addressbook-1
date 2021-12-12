pipeline{
    agent any
    tools{
        maven 'mymaven'
        jdk 'myjava'
    }
    stages{
        stage("compile"){
            steps{
                script{
                    echo "Compiling the code"
                    sh 'mvn compile'

                }

            }

        }
        stage("test"){
            steps{
                script{
                    echo "Testing the code"
                    sh 'mvn test'


                }

            }
            post{
                always{
                    junit 'target/surefire-reports/*.xml'
                }
            }

        }
        stage("package"){
            steps{
                script{
                    echo "Packaging the code"
                    sh 'mvn package'

                }

            }

        }
        stage("build the docker image"){
            steps{
                script{
                    echo "building the docker image"
                    withCredentials([usernamePassword(credentialsId: 'docker-hub', passwordVariable: 'pswd', usernameVariable: 'user')]) {
                    sh 'sudo docker build -t saikiranreddy1808/java-mvn-privaterepos:$BUILD_NUMBER .'
                    sh 'sudo docker login -u $user -p $pass'
                    sh 'sudo docker push saikiranreddy1808/java-mvn-privaterepos:$BUILD_NUMBER'
                 
}
                }
            }
        }
        stage('deploy the docker container'){
            steps{
                script{
                    echo "deploy the app"
                    sh 'sudo docker run -itd -P saikiranreddy1808/java-mvn-privaterepos:$BUILD_NUMBER'
                }
            }
        }

        
    }
}