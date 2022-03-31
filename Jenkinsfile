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

        stage('Sonar') {
          steps {
            waitForQualityGate(abortPipeline: true)
          }
        }

      }
    }

    stage('Run') {
      steps {
        sh 'java -jar target/*.jar --server.port=9090'
      }
    }

  }
}