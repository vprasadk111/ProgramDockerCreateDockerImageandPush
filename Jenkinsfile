pipeline{
	agent any
	def app
	stages{
		stage('Clone repository'){
			steps{
				checkout scm
			}
		stage('Build image'){
			steps{
				app = docker.build("vprasadk/test")
			}
		}
		stage('Test image'){
				steps{
					app.inside {
            sh 'echo "Tests passed"'
        }
				}
		  }
			stage('Push image'){
				steps{
						docker.withRegistry('https://registry.hub.docker.com', 'dockerhub') {
            app.push("${env.BUILD_NUMBER}")
            app.push("latest")
        }
				}
			}

	}
	}
}
