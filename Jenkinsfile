//Declare variable

pipeline { 

  environment { 

      registry = "vprasadk/programdockercontainer" 

      registryCredential = 'dockerhub' 

      dockerImage = '' 

  }

  agent any 

  stages { 

      stage('Clone Git') { 

          steps { 

              git 'https://github.com/vprasadk111/ProgramDockerCreateDockerImageandPush.git' 

          }

      } 

      stage('Building the image') { 

          steps { 

              script { 

                  dockerImage = docker.build registry + ":$BUILD_NUMBER" 

              }

          } 

      }
    
    
    *****//
    
          stage('Container start') { 

          steps { 

              script { 

                  //dockerImage = docker.build registry + ":$BUILD_NUMBER" 
                sh 'docker run -p 5000:5000 -d vprasadk/programdockercontainer:$BUILD_NUMBER'

              }

          } 

      }
    
    //******

      stage('Push Image to Docker Hub') { 

          steps { 

              script { 

                  docker.withRegistry( '', registryCredential ) { 

                      dockerImage.push() 

                  }

              } 

          }

      } 
    
    stage('Remove Image') { 
31
            steps { 
32
                sh "docker rmi $registry:$BUILD_NUMBER" 
33
            }
34
        } 


  }

}
