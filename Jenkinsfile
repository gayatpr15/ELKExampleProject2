node {
	def application = "springbootapp"
	
	stage('Clone repository') {
		checkout scm
	}

	stage('Build image') {
		app = docker.build("${application}:${BUILD_NUMBER}")
	}


	stage('Deploy') {
		sh ("docker run -d -p 86:8080 -v /var/log/:/var/log/ ${application}:${BUILD_NUMBER}")
			}
	
	
	
environment {
		DOCKERHUB_CREDENTIALS=credentials('dockerhub-cred-gayatpr')
	}
	
	

		stage('Build') {

			
				sh 'docker build -t springbootapp:${BUILD_NUMBER} .'
			
		}
		stage('tag') {

					sh 'docker tag springbootapp:${BUILD_NUMBER} gayatpr15/springbootapp:${BUILD_NUMBER}'
		}
		stage('Login123') {
				sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR tiadha123!!$$$'
			
		}
		stage('Push123') {
			
				sh 'docker push gayatpr15/springbootapp:${BUILD_NUMBER}'
			
		}


	
}
