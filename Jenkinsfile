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
				echo 'Git Message JIRA Id status:' + GIT_COMMIT_JIRA_ID
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