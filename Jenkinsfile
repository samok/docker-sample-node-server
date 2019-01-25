pipeline {
	agent none
	stages {
		stage('Build node-app') {
			agent any
			steps {
				sh 'docker build --rm -t samok/node-web-app .'
			}
		}
		stage('Deploy app on node') {
			agent any
			steps {
				sh 'docker run -p 8090:8090 -itd samok/node-web-app > ${WORKSPACE}/container_id'
				sh 'ls -a ${WORKSPACE}'
				sh 'cat ${WORKSPACE}/container_id'

			}
		}
		stage('Stop container') {
			agent any
			steps {
				sh 'echo The End'
				sh 'echo right'
			}
		}
	}
}