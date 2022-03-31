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

    stage('Out') {
      steps {
        echo 'Success'
      }
    }

  }
}