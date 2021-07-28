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

			 sh 'docker login -u kumudhanrajan18@gmail.com -p "Chok3$lam" https://registry.hub.docker.com'
          		 sh 'docker push kumudhan/jenkins_build_images:1.0.0'
                  }

              } 

          }

      } 

  
}

