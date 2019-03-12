#!/usr/bin/env groovy

pipeline {
	agent any
	environment {
		CLEAN_BRANCH_NAME = "${BRANCH_NAME.replace('/', '-')}"
		GIT_TAG = sh(returnStdout: true, script: "git tag --contains").trim()
	}
	stages {
		stage('Deploy') {
			parallel {
				stage('Release') {
					when {
						buildingTag()
					}
					steps {
						sh 'mvn --batch-mode versions:set -DnewVersion=${GIT_TAG}'
						sh 'mvn --batch-mode deploy'
					}
				}
				stage('Snapshot') {
					when {
						not { buildingTag() }
					}
					steps {
						sh 'mvn --batch-mode versions:set -DnewVersion=${CLEAN_BRANCH_NAME}-SNAPSHOT'
						sh 'mvn --batch-mode deploy'
					}
				}
			}
		}
	}
}
