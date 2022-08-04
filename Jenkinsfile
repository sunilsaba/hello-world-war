pipeline {
    agent any	
	 
 stages {
      stage('checkout') {
           steps {             
                git branch: 'master', url: 'https://github.com/sunilsaba/hello-world-war.git'             
          }
        }       

  stage('Docker Build and Tag') {
           steps {  
		 
                sh 'sudo docker build -t testwebapp:latest .' 
                
            }
        }

stage('Login to Docker hub') {
           steps {
              
                sh 'sudo docker login --username=sunikdocker --password=8123059361Ss$'
                sh 'sudo docker tag testwebapp:latest sunikdocker/testwebapp:latest'
          }
        }
     
  stage('Publish image to Docker Hub') {
          
            steps {
       	  sh  'sudo docker push sunikdocker/testwebapp:latest'  
        }                 
          
        }
stage('pull') {
            steps {
                sh 'sudo docker pull sunikdocker/testwebapp:latest'
            }
        }     
      stage('Run Docker container on Jenkins Agent') {
             
            steps 
	      {
                sh "sudo docker run -d -p 8004:8080 sunikdocker/testwebapp:latest"
             }
        }
 
    }
	}
