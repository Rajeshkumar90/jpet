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
  }
}