node {
	def application = "springbootapp"
	environment {
		DOCKERHUB_CREDENTIALS=credentials('dockerhub-cred-gayatpr')
	}
	

	stage('Clone repository') {
		checkout scm
	}

	stage('Build image') {
		app = docker.build("${application}:${BUILD_NUMBER}")
	}


	stage('Deploy') {
		sh ("docker run -d -p 85:8080 -v /var/log/:/var/log/ ${application}:${BUILD_NUMBER}")
			}
	
	
	
	

		stage('Build') {

			
				sh 'docker build -t ${application}:${BUILD_NUMBER} .'
			
		}
		stage('Login') {
				sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
			
		}
		stage('tag') {

			sh 'docker tag ${application}:${BUILD_NUMBER} gayatpr15/springbootapp:${BUILD_NUMBER}
		}
		
		stage('Push') {
			sh 'docker push gayatpr15/springbootapp:${BUILD_NUMBER}'
			
		}
	


	
}
