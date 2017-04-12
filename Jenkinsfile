pipeline {
  agent any
  stages {
        stage ('SCM') {
            steps {
                bat(script: 'echo "SCM Completed"', returnStatus: true)
            }
        }              
        stage ('Build') {
            steps {
                bat(script: 'echo "Build completed succesfully"', returnStatus: true)
            }
        }
        stage ('Analysis') {
            steps {
                bat(script: 'echo "Build analysis completed succesfully"', returnStatus: true)
            }
        }
        stage ('CF push') {
            steps {
                bat(script: 'echo "Pused the app succesfully"', returnStatus: true)
            }
        }
        stage ('Test') {
            steps {
                bat(script: 'echo "triger"', returnStatus: true, returnStdout: true)
            }
        }                            
    }
	post {
            success {
                bat(script: 'echo "mapped route"', returnStatus: true, returnStdout: true)
            }
                                
        }
}
