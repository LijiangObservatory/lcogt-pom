#!/usr/bin/env groovy

pipeline {
	agent any
	environment {
		CLEAN_BRANCH_NAME = "${BRANCH_NAME.replace('/', '-')}"
		SITE_SOFTWARE_VERSION = "${CLEAN_BRANCH_NAME}-SNAPSHOT"
	}
	stages {
		stage('Set version') {
			when {
				not { branch 'master' }
			}
			steps {
				sh 'mvn versions:set -DnewVersion=${SITE_SOFTWARE_VERSION}'
			}
		}
		stage('Deploy') {
			steps {
				sh 'mvn deploy'
			}
		}
	}
}
