pipeline {
    agent {
        docker {
            image 'ruby'
        }
    }
    
    stages {
        stage ('Build') {
			steps {
				echo 'Building or Resolve Dependencies'
                sh 'bundle install'
 			}
		}
		stage ('Test') {
			steps {
				echo 'Running Regression tests'
			}
		}
		stage ('UAT') {
			steps {
				echo 'Wait for user Acceptance'
				input(message: 'Go To Production', ok: 'Yes')
			}
		}
		stage ('Prod') {
			steps {
				echo 'WebAPP is Ready :)'
			}
		}
	}
}