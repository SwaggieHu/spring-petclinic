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

    stage('sonar') {
      steps {
        withSonarQubeEnv(installationName: 'sonar', envOnly: true)
      }
    }

    stage('build') {
      steps {
        sh './mvnw package'
      }
    }

  }
}