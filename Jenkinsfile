pipeline {
  agent any

  tools {
    maven 'M3'
    jdk 'JDK21'
  }

  stages {
    stage('Checkout') {
      steps {
        checkout scm
      }
    }

    stage('Build') {
      steps {
        bat 'mvn -B clean package'
      }
    }

    stage('Archive') {
      steps {
        archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
      }
    }
  }

  post {
    success { echo "Build Succeeded: ${env.BUILD_URL}" }
    failure { echo "Build Failed" }
  }
}

