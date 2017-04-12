pipeline {
  agent any
  stages {
    stage('SCM') {
      steps {
        bat(script: 'echo "SCM Completed"', returnStatus: true)
      }
    }
    stage('Build') {
      steps {
        echo 'Build completed succesfully'
      }
    }
    stage('CF push') {
      steps {
        echo 'Pushed successfully'
      }
    }
    stage('Test') {
      steps {
        bat(script: 'echo "triger"', returnStatus: true, returnStdout: true)
      }
    }
  }
}