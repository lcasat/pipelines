pipeline {
	agent any
	parameters {
		booleanParam (
            defaultValue: false,
            description: 'Git Commit Message JIRA Id',
            name : 'GIT_COMMIT_JIRA_ID')
	}
	stages {
		stage("Fetch") {
			steps {
				echo 'Getting lastest commit message...'
				script {
					def commit_message = sh(script:"git log --pretty='format:%Creset%s' --no-merges -1", returnStdout: true)
                	print commit_message
                	containsJiraLink = (commit_message ==~ /^.*(?:https:?\/\/)?[\w.-]+\/[\w]+\/[A-Z-]+[\d]+.*$/)
                    print containsJiraLink
				}
				GIT_COMMIT_JIRA_ID = containsJiraLink
				echo 'Git Message JIRA Id status:' + GIT_COMMIT_JIRA_ID
				return GIT_COMMIT_JIRA_ID
			}
		}
		stage("Validate") {
			steps {
				echo 'Validating lastest commit message...'
			}
		}
		stage("Unit Tests") {
			steps {
				echo 'Unit tests stage..'
			}
		}
	}
}