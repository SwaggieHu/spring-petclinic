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

    stage('build') {
      steps {
        sh './mvnw package'
      }
    }

    stage('sonar') {
      steps {
        waitForQualityGate true
        withSonarQubeEnv(installationName: 'sonar', envOnly: true)
      }
    }

  }
}