pipeline {
	agent none
	stages {
		stage('Build node-app') {
			agent { docker 'node:8' }
			steps {
				sh 'docker build --rm -t samok/node-wb-app .'
			}
		}
		stage('Deploy app on node') {
			agent any
			steps {
				sh 'docker run -p 8090:8090 -itd samok/node-wb-app > container_id'
			}
		}
	}
}