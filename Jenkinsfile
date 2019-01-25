pipeline {
	agent any
	stages {
		stage('Build node-app') {
			steps {
				sh 'docker build --rm -t samok/node-wb-app .'
			}
		}
		stage('Deploy app on node') {
			steps {
				sh 'docker run -p 8090:8090 samok/node-wb-app'
			}
		}
	}
}