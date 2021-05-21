pipeline {
    
  agent any
  
  
  stages {
       
        stage('Git Clone Code') {
           steps {
                script {
                          git branch: env.GIT_BRANCH, url: 'https://github.com/zjexteer/my_project.git'
                }
           }
        }

        

    
        stage(' build') {


          steps {
             script{    
                    dockerImage = docker.build 'mawlstace/my-nginx:' +${env.GIT_BRANCH} 
                    docker.withRegistry( '', 'docker_hub' ) { 
                        dockerImage.push()
                        } 
             }
          } 
        }
  }

}

