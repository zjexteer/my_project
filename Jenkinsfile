pipeline {
    
  agent any
  
  
  stages {
  parameters {
    choice(name:'env', choices: ['dev','test' , 'prod'] )
  }

       
        stage('Git Clone Code') {
           steps {
                script {
                          git branch: params.env, url: 'https://github.com/zjexteer/my_project.git'
                }
           }
        }

        

    
        stage(' build') {


          steps {
             script{    
                    dockerImage = docker.build 'mawlstace/my-nginx:' +params.env 
                    docker.withRegistry( '', 'docker_hub' ) { 
                        dockerImage.push()
                        } 
             }
          } 
        }
  }

}

