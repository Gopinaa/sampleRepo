pipeline{
	agent any
	
	environment {
		NEW_VERSION='1.0.3'
		SERVER_CREDENTIALS=credentials('server-creds')
		
		
	}
	
	stages {
		stage("build") {
			steps {
				echo 'this is build file'
				echo "Version  ${NEW_VERSION}"
			}
		}
		stage("test") {
			steps {
				echo 'this is test file'
				echo " credentials &{SERVER_CREDENTIALS}"
				sh "SERVER_CREDENTIALS"
			}
		}
		stage("deploy") {
			steps {
				echo 'this is deploy file'
							
				withCredentials([
					userNamePassword(credentials:'server-creds',userNmaeVariable:USER,passwordVariable:PWD)
				]){
					sh "some script ${USER} ${PWD}"
				
				}
			}
		}
	}
}
