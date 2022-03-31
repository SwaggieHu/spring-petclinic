pipeline {
  agent any
  stages {
    stage('Environment Check') {
      parallel {
        stage('Environment Check') {
          steps {
            sh '''mvn -version
java -version
git --version'''
          }
        }

        stage('') {
          steps {
            withSonarQubeEnv(installationName: 'sonar', envOnly: true)
          }
        }

      }
    }

    stage('Build') {
      steps {
        sh './mvnw package'
      }
    }

    stage('sonar') {
      steps {
        waitForQualityGate true
      }
    }

  }
}