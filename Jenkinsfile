node {
	def application = "springbootapp"
	

	stage('Clone repository') {
		checkout scm
	}

	stage('Build image') {
		app = docker.build("${application}:${BUILD_NUMBER}")
	}


	stage('Deploy') {
		sh ("docker run -d -p 81:8080 -v /var/log/:/var/log/ ${application}:${BUILD_NUMBER}")
		
	}
	
	stages {

		stage('Build') {

			steps {
				sh 'docker build -t gayatpr15/${application}:${BUILD_NUMBER} .'
			}
		}

		stage('Login') {

			steps {
				sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
			}
		}

		stage('Push') {

			steps {
				sh 'docker push gayatpr15/${application}:${BUILD_NUMBER}'
			}
		}
	}


	
}
