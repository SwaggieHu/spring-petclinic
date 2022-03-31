pipeline {
  agent any
  stages {
    stage('Environment Check') {
      steps {
        sh '''mvn -version
java -version
git --version'''
      }
    }

    stage('Build') {
      parallel {
        stage('Build') {
          steps {
            sh './mvnw package'
          }
        }

        stage('sonar prepare') {
          steps {
            withSonarQubeEnv 'sonar'
          }
        }

      }
    }

    stage('sonar') {
      steps {
        waitForQualityGate true
      }
    }

  }
}