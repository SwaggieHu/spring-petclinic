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

    stage('run') {
      steps {
        sh 'java -jar target/*.jar --server.port=9090'
      }
    }

  }
}