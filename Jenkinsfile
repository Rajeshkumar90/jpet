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
        bat(script: 'echo "Build completed succesfully"', returnStatus: true)
      }
    }
    stage('Analysis') {
      steps {
        bat(script: 'echo "Build analysis completed succesfully"', returnStatus: true)
      }
    }
    stage('CF push') {
      steps {
        bat(script: 'echo "Pused the app succesfully"', returnStatus: true)
      }
    }
    stage('Test') {
      steps {
        script {
			try {
				bat "echo test suite is completed"
			}catch(err) {
				try {
					timeout(time: 15, unit: 'SECONDS') {
					public def userInput = input(id: 'UserInput', message: 'Approval ', parameters: [[$class: 'TextParameterDefinition', defaultValue: 'Yes', description: 'Approval', name: 'Approval']])
					env.ENV = userInput
					}
				} catch (err1) {
					CF_app()
					return
				}
				if ( env.ENV  == "Yes") {
					CF_app()
					return
				} else {	
					currentBuild.result = 'FAILURE'
					return
				}
			} 
			CF_app()
			def CF_app() {
			stage 'Map route'
			bat "echo Mapped the route"
			stage 'Unmap route'
			bat "echo Unmapped the route"
			stage 'Delete app'
			bat "echo Deleted the app"
			stage 'Promote'
			parallel (CloudFoundry_push_to_QA: {
				bat "echo Successfully pushed to QA env"
				build job: 'Deploy to QA'
				}, Cloud_Foundry_push_to_UAT: {
				bat "echo Successfully pushed to UAT env"
				build job: 'Deploy to UAT'
				}, Cloud_Foundry_push_to_INT: {
				bat "echo Successfully pushed to INT env"
				build job: 'Deploy to INT'
				})
			}
        }
      }
    }
  }
}
