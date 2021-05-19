//Orginal

node {
def app
	
stage('Confirmation') {
input('Do you really want to proceed with ?')
}
	
	
stage('Clone repository') {
checkout scm
}

stage('Build image') {
app = docker.build("vprasadk/programdockercreatedockerimageandpush")
}

stage('Test image') {
app.inside {
sh 'echo " Image Created !!! "'
}
}

stage('Run Container') {
            steps {
                sh 'docker run -p 5000:5000 -d vprasadk/programdockercreatedockerimageandpush:latest'
            }

stage('Push image') {
	//dockerhub - ID given while creating Docker Hub user
docker.withRegistry('https://registry.hub.docker.com', 'dockerhub') {
app.push("${env.BUILD_NUMBER}")
app.push("latest")
}
}
}
