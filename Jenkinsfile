//Orginal

node {
def app

//Giving confirmation to the job.
	
stage('Confirmation') {
input('Do you really want to proceed with ?')
}

//Clone repo from GitHub
	
stage('Clone repository') {
checkout scm
}

	
//Building the image
	
stage('Build image') {
app = docker.build("vprasadk/programdockercreatedockerimageandpush")
}

//Testing the image
	
stage('Test image') {
app.inside {
sh 'echo " Image Created !!! "'
}
}
	
//Starting the container

stage('Start Container') {
           
sh 'docker run -p 5000:5000 -d vprasadk/programdockercreatedockerimageandpush:latest'
}

//Pusing the image to Docker Hub
	
stage('Push image') {
	//dockerhub - ID given while creating Docker Hub user
docker.withRegistry('https://registry.hub.docker.com', 'dockerhub') {
//app.push("${env.BUILD_NUMBER}")
app.push("latest")
//}
//}
}
