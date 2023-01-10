pipeline {
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
        stage('Test') {
          parallel {

            stage('Test'){
            steps {
            sh 'mvn test'
            }
            }
               stage('Download') {
                   steps {
                   archiveArtifacts artifacts: 'build/libs/**/*.jar', fingerprint: true
                    junit 'build/reports/**/*.xml'
                     }
                    }
          }
        }
        stage('Package') {
            steps {
            sh 'mvn package'
            }
        }
        stage('Download') {
          steps {
          archiveArtifacts artifacts: 'build/libs/**/*.jar', fingerprint: true
          junit 'build/reports/**/*.xml'
          }
        }
    }
    post {
          always  {
           archiveArtifacts artifacts: 'build/libs/**/*.jar', fingerprint: true
           junit 'build/reports/**/*.xml'
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
