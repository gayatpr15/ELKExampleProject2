
node {
	def application = "springbootapp"
	def dockerhubaccountid = "gayatpr15"

	stage('Clone repository') {
		checkout scm
	}

	stage('Build image') {
		app = docker.build("${dockerhubaccountid}/${application}:${BUILD_NUMBER}")
	}
	
	

	stage('Deploy') {
		sh ("docker run -d -p 83:8080 -v /var/log/:/var/log/ ${dockerhubaccountid}/${application}:${BUILD_NUMBER}")
		
	}

	
}

