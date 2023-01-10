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
            steps {
            sh 'mvn test'
            }
        }
        stage('Package') {
            steps {
            sh 'mvn package'
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
