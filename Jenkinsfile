containsJiraLink = false

pipeline {
	agent any
	stages {
		stage("Get the Git Commit Message") {
			steps {
				echo 'Getting lastest commit message...'
				script {
					def commit_message = sh(script:"git log --pretty='format:%Creset%s' --no-merges -1", returnStdout: true)
                	print commit_message
                	containsJiraLink = (commit_message ==~ /^.*(?:https:?\/\/)?[\w.-]+\/[\w]+\/[A-Z-]+[\d]+.*$/)
                    print containsJiraLink
				}
			}
		}
		stage("Validate Git Commit Message") {
			steps {
				echo 'Validating lastest commit message...'
				script {
                    if (!containsJiraLink) 
                        currentBuild.result = 'FAILURE'
                        echo 'Further code will not be executed'
                    }   
                }
			}
		}
		Stage("Run Unit Tests") {
			steps {
				echo 'Running unit tests..'
			}
		}
	}
}
