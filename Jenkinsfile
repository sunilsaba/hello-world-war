pipeline {
    agent any	
	 
 stages {
      stage('checkout') {
           steps {             
                git branch: 'master', url: 'https://github.com/sagartnaik/hello-world-war.git'             
          }
        }       

  stage('Docker Build and Tag') {
           steps {  
		 
                sh 'sudo docker build -t testwebapp:latest .' 
                
            }
        }

stage('Login to Docker hub') {
           steps {
              
                sh 'sudo docker login --username=sagartnaikdocker --password=Sagar@3692'
                sh 'sudo docker tag testwebapp:latest sagartnaikdocker/testwebapp:latest'
          }
        }
     
  stage('Publish image to Docker Hub') {
          
            steps {
       	  sh  'sudo docker push sagartnaikdocker/testwebapp:latest'  
        }                 
          
        }
stage('pull') {
            steps {
                sh 'sudo docker pull sagartnaikdocker/testwebapp:latest'
            }
        }     
      stage('Run Docker container on Jenkins Agent') {
             
            steps 
	      {
                sh "sudo docker run -d -p 8004:8080 sagartnaikdocker/testwebapp:latest"
             }
        }
 
    }
	}
