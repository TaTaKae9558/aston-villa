pipeline {
    agent any
    tools {
        maven 'maven '
    }
    stages {
        stage('Build') {
            steps {
                bat 'mvn clean package'
            }
             post {
               always {
                    junit 'target/surefire-reports/*.xml'
            }
        }
        stage('Run Test') {
            steps {
                bat 'mvn test'
            }
        }
    }
   }
}
