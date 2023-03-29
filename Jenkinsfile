
node {
	def application = "springbootapp"
	def dockerhubaccountid = "gayatpr15"

	stage('Clone repository') {
		checkout scm
	}

	stage('Build image') {
		app = docker.build("${dockerhubaccountid}/${application}:${BUILD_NUMBER}")
	}
	
	stage('Push image') {
		withDockerRegistry([ credentialsId: "dockerHub", url: "docker.io/${dockerhubaccountid}/${application}:${BUILD_NUMBER}" ]) {
		app.push()
		app.push("latest")
	}
	}

	stage('Deploy') {
		sh ("docker run -d -p 83:8080 -v /var/log/:/var/log/ ${dockerhubaccountid}/${application}:${BUILD_NUMBER}")
		
	}

	
}

