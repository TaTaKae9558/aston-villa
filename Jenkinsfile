pipeline {
    agent any
  tools {
    maven 'maven'
  }

    stages {
        stage('Build') {
      steps {
        bat 'mvn clean package'
      }
        }

    stage('Run tests') {
      steps {
        bat 'mvn test'
      }

      post {
        always {
          junit 'target/surefire-reports/*.xml'
        }
      }
    }
        stage('SonarQube analysis') {
          steps {
            script {
            withSonarQubeEnv(installationName: 'sonar', credentialsId: 'jenkins-sonar-token') {
            bat 'mvn sonar:sonar'
            }
            }
          }
        }
    }
}
