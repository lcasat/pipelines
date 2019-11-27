containsJiraLink = false

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
				echo 'Git Message JIRA Id status 1:' + GIT_COMMIT_JIRA_ID
				script {
                    def commit_message = sh(script:"git log --pretty='format:%Creset%s' --no-merges -1", returnStdout: true)
                    print commit_message
                    containsJiraLink = (commit_message ==~ /^.*(?:https:?\/\/)?[\w.-]+\/[\w]+\/[A-Z-]+[\d]+.*$/)
                    print containsJiraLink
                }
                params.GIT_COMMIT_JIRA_ID = containsJiraLink
                echo 'Git Message JIRA Id status 2:' + GIT_COMMIT_JIRA_ID
			}
		}
		stage("Validate") {
			steps {
				echo 'Validating lastest commit message...'
			}
		}
		stage("UnitTests") {
			steps {
				echo 'Unit tests stage..'
			}
		}
	}
}