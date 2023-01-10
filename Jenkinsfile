
pipeline{

    agent any

    tools { 

        maven 'Maven'

    }

    stages

       {

            stage("clean")

            {

                steps{

                    sh "mvn clean"

                }

            }

            stage("Build")

            {

                steps{

                    sh "mvn compile"

                }

                

            }

            stage("TEST")

            {

                steps{

                    sh "mvn test"

                }

            }

            stage("package")

            {

                steps{

                    sh "mvn package"

                }

            }

        

    }
    post {
      always  {
        archiveArtifacts 'build/libs/**/*.jar'
        }        
       success{
            emailext to: "akash.kumar@knoldus.com",
            subject: "Test Email Sucess",
            body: "Test Success"
        }
        
        failure{
            emailext to: "akash.kumar@knoldus.com",
            subject: "Test Email Failure",
            body: "Test Failure"
        } 
    }

}
