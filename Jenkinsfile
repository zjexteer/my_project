pipeline {
    
  agent any
  
  
  stages {

       
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
                     withCredentials([string(credentialsId: 'mawlstace', variable: 'CREDS')]) {
				sh 'docker login -u mawlstace -p ${CREDS}'
			}
   sh ' docker build -t mawlstace/my-nginx:${params.env}'
   sh ' docker push '              
}
          } 
        }
  }

}

