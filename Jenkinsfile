pipeline {
    agent { docker { image 'maven:3.8.7-eclipse-temurin-11' } }
    stages {
        stage('build') {
            steps {
                sh 'echo "Building"'
                sh 'mvn clean package'
            }
        }
          stage('test') {
            steps {
                sh 'mvn test'
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
