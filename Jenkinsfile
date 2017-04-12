	node  {
					stage 'SCM'
					bat 'echo SCM built successfully'
					stage 'Build'
					bat 'echo Build built successfully'
					stage 'Analysis'
					bat 'echo Build Analysis successfully'				
					stage 'CF push'
					bat 'echo CF push Analysis successfully'				
					stage 'Test'
					try {
		
									bat "echoe test suite is completed"
					}catch(err) {
						try {
							timeout(time: 15, unit: 'SECONDS') {
								public def userInput = input(id: 'UserInput', message: 'Approval ', parameters: [[$class: 'TextParameterDefinition', defaultValue: 'Yes', description: 'Approval', name: 'Approval']])
								env.ENV = userInput
							}
						} catch (err1) {
							stage 'Map route2'
							bat "echo Mapped the route2"
							stage 'Unmap route2'
							bat "echo Unmapped the route2"
							stage 'Delete app2'
							bat "echo Deleted the app2"
							stage 'Promote2'
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
							return
						}
						if ( env.ENV  == "Yes") {
							stage 'Map route1'
							bat "echo mapped the route1"
							stage 'Unmap route1'
							bat "echo Unmapped the route1"
							stage 'Delete app1'
							bat "echo Deleted the app1"
							stage 'Promote1'
							parallel (CloudFoundry_push_to_QA: {
								bat "echo Successfully pushed to QA env"
								build job: 'Deploy to QA'
								}, Cloud_Foundry_push_to_UAT: {
								//stage 'Cloud Foundry push to UAT'
								bat "echo Successfully pushed to UAT env"
								build job: 'Deploy to UAT'
								}, Cloud_Foundry_push_to_INT: {
								//stage 'Cloud Foundry push to INT'
								bat "echo Successfully pushed to INT env"
								build job: 'Deploy to INT'
								})
								return
						} else {	
							currentBuild.result = 'FAILURE'
							return
						}
						
					} 
					stage 'Map route3'
					bat "echo mapped route3"
					stage 'Unmap route3'
					bat "echo Unmapped the route3"
					stage 'Delete app3'
					bat "echo Deleted the app3"
					stage 'Promote3' 
					parallel (CloudFoundry_push_to_QA: {
									bat "echo Successfully pushed to QA env"
									build job: 'Deploy to QA'
					}, Cloud_Foundry_push_to_UAT: {
					//stage 'Cloud Foundry push to UAT'
									bat "echo Successfully pushed to UAT env"
									build job: 'Deploy to UAT'
						
					}, Cloud_Foundry_push_to_INT: {
					//stage 'Cloud Foundry push to INT'
									bat "echo Successfully pushed to INT env"
									build job: 'Deploy to INT'
					})
	}
