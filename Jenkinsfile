#!/usr/bin/env groovy

@Library('lco-shared-libs@0.1.0') _

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
