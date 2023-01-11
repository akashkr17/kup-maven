pipeline {
     options {
          buildDiscarder(logRotator(numToKeepStr: '10', artifactNumToKeepStr: '20'))
      }
    agent any
     tools {
          maven 'Maven'

     }
    stages {
        stage('Clean') {
            steps {
                sh 'mvn clean'
            }
        }
        stage('Build') {
            steps {
             sh 'mvn compile'
             }
        }
        stage('Testing') {
          parallel {

            stage('Test on Linux '){
              steps {
               sh 'mvn test'
              }
            }
             stage('Testing on Window') {
              steps {
                sh 'echo "Testing on windows"'
                }
              }
          }
        }
        stage('Package') {
            steps {
            sh 'mvn package'
            }
             post {
                success {
                  archiveArtifacts artifacts: 'target/*.jar, target/*.war'
                }
             }
        }
    }
    post {
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
