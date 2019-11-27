pipeline {
	agent any
	stages {
		stage("Get the Git Commit Message") {
			steps {
				echo 'Getting lastest commit message...'
				def commit_message = sh(script:"git log --pretty='format:%Creset%s' --no-merges -1", returnStdout: true)
                print commit_message
			}
		}
		stage("Validate Git Commit Message") {
			steps {
				echo 'Validating lastest commit message...'
			}
		}
	}
}
