containsJiraLink = false
commit_message = ''
pipeline {
	agent any
	
	stages {
		stage("Fetch") {
			steps {
				echo 'Getting lastest commit message...'
				script {
                    def commit_message = sh(script:"git log --pretty='format:%Creset%s' --no-merges -1", returnStdout: true)
                    print commit_message
                }
			}
		}
		stage("Validate") {
			steps {
				echo 'Validating lastest commit message...'
				script {
					containsJiraLink = (commit_message ==~ /^.*(?:https:?\/\/)?[\w.-]+\/[\w]+\/[A-Z-]+[\d]+.*$/)
                    print containsJiraLink
                    if (!containsJiraLink) {
						error "This pipeline stops here!"
					}
				}
			}
		}
		stage("UnitTests") {
			steps {
				echo 'Unit tests stage..'
			}
		}
	}
}