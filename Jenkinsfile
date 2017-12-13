#!/usr/bin/env groovy

pipeline {
	agent any
	options {
		buildDiscarder(
			logRotator(
				numToKeepStr: '10'
			)
		)
	}
	stages {
		stage('Deploy') {
			steps {
				checkout scm
				sh 'mvn deploy'
			}
		}
	}
}
