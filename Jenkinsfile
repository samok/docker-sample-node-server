pipeline {
	agent none
	stages {
		// Construction d'une app node.js
		stage('Build App') {
			agent any
			steps {
				sh 'docker build --rm -t samok/node-web-app .'
			}
		}
		//Deploiement sur un container docker node.js
		stage('Deploy App on container') {
			agent any
			steps {
				sh 'docker run -p 8090:8090 -itd samok/node-web-app > ${WORKSPACE}/container_id'
				sh 'docker exec -t ${WORKSPACE}/container_id bash'
				sh 'npm install @angular/cli'
			}
		}
		// Lancer la batteries de tests sur la plateforme
		stage('Test App') {
		}
		// Arreter et detruire le container
		stage('Stop and Clean container') {
			agent any
			steps {
				sh 'docker stop $(cat ${WORKSPACE}/container_id)'
				sh 'docker rm $(cat ${WORKSPACE}/container_id)'
			}
		}
	}
}