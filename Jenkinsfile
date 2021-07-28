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

                  dockerImage = docker.build("kumudhan/jenkins_build_images:${env.BUILD_ID}")

              }

          } 

      }

      stage('Deploy our image') { 

          steps { 

              script {

                  docker.withRegistry('https://registry.hub.docker.com', 'dockerhub') {

                      dockerImage.push("latest")
		      dockerImage.push("${env.BUILD_ID}")

                  }

              } 

          }

      } 

  }
}

