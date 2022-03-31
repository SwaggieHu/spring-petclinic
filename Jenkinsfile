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
      steps {
        sh './mvnw package'
      }
    }

    stage('Run') {
      steps {
        sh 'java -jar target/*.jar --server.port=9090'
      }
    }

  }
}