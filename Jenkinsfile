pipeline{

	agent any

	environment {
		DOCKERHUB_CREDENTIALS=credentials('dockerhub')
	}

	stages {
	    
	    stage('gitclone') {

			steps {
				git 'https://github.com/BharathSharath/Node-Redis-Mongo-app.git'
			}
		}

		stage('Build') {

			steps {
				sh 'docker build -t bharathsharath/node:latest .'
			}
		}

		stage('Login') {

			steps {
				sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
			}
		}
		
		stage('Push') {

			steps {
				sh 'docker push bharathsharath/node:latest'
			}
		}
	}

	post {
		always {
			sh 'docker logout'
		}
	}

}
