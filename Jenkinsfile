pipeline { 	

  environment { 

      registry = "kumudhan/jenkins_build_images" 

      registryCredential = 'dockerhub' 

      dockerImage = '' 

  }

  agent any 

  stages { 

      stage('Cloning our Git') { 

          steps { 

              git 'https://github.com/kumudhanrajan18/Knote_jenkins_k8.git' 

          }

      } 

      stage('Building our image') { 

          steps { 

              script { 

                  dockerImage = docker.build registry + ":$BUILD_NUMBER" 

              }

          } 

      }

      stage('Deploy our image') { 

          steps { 

              script { 

                  docker.withRegistry( '', registryCredential ) { 

                      dockerImage.push() 

                  }

              } 

          }

      } 

  }
}

