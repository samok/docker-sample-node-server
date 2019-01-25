pipeline {
	agent none
	stages {
		stage('Build node-app') {
			agent { docker 'node:8' }
			steps {
				sh 'docker build --rm -t samok/node-web-app .'
			}
		}
		stage('Deploy app on node') {
			agent any
			steps {
				sh 'docker run -p 8090:8090 -itd samok/node-web-app > container_id'
				sh 'cat container_id'
			}
		}
	}
}