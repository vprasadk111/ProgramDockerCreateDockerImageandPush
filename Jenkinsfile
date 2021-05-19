pipeline { 

environment { 

    registry = "vprasadk/programdockercontainer" 

    registryCredential = 'dockerhub' 

    dockerImage = '' 

}

agent any 

stages { 

    stage('Cloning our Git') { 

        steps { 

            git 'https://github.com/vprasadk111/ProgramDockerCreateDockerImageandPush.git' 

        }

    } 

    stage('Building our image') { 

        steps { 

            script { 

                dockerImage = docker.build registry + ":$BUILD_NUMBER" 

            }

        } 

    }
    
     //
    
          stage('Container start') { 

          steps { 

              script { 

                  //dockerImage = docker.build registry + ":$BUILD_NUMBER" 
                sh 'docker run -p 5000:5000 -d vprasadk/programdockercontainer:$BUILD_NUMBER'

              }

          } 

      }
    
    //

    stage('Deploy our image') { 

        steps { 

            script { 

                docker.withRegistry( '', registryCredential ) { 

                    dockerImage.push() 

                }

            } 

        }

    } 

    stage('Cleaning up') { 

        steps { 

            sh "docker rmi $registry:$BUILD_NUMBER" 

        }

    } 

}

}
