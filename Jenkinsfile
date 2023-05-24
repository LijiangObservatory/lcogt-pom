#!/usr/bin/env groovy

@Library('lco-shared-libs@0.2.0') _

pipeline {
	agent any
	stages {
		stage('Deploy') {
			steps {
				sh 'mvn --batch-mode deploy'
			}
		}
	}
	post {
		always { postBuildNotify() }
	}
}
