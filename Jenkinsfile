//Orginal

node {

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
	
  sh 'docker build -t vprasadk/programdockercreatedockerimageandpush:0.0.1 .'
}

	
//Starting the container

stage('Start Container') {
           
sh 'docker run -p 5000:5000 -d vprasadk/programdockercreatedockerimageandpush:0.0.1'
}

}
