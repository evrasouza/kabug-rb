pipeline {
    agent {
        docker {
            image 'qaninja/rubywd'
        }
    }
    
    stages {
        stage ('Build') {
			steps {
				echo 'Building or Resolve Dependencies'
				sh 'rm -f Gemfile.lock'
				sh 'bundle install'
 			}
		}
		stage ('Test') {
			steps {
				echo 'Running Regression tests'
				sh 'bundle exec cucumber -p ci'
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