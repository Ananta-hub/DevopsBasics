pipeline {
    agent any
 
   tools
    {
       maven "apache-maven-3.8.1"
    }
 stages {
      stage('checkout') {
           steps {
             
                git branch: 'master', url: 'https://github.com/Ananta-hub/DevopsBasics.git'
             
          }
        }
  stage('Execute Maven') {
           steps {
             
                sh 'mvn package'             
          }
        }
stage('Docker Build and Tag') {
           steps {
              
                sh '  docker build -t cutomimage .'
               
          }
        }
     
 stage('Run Docker container on remote hosts') {
             
            steps {
                sshagent(['Application']) {
                  sh "docker -H ssh://ec2-user@172.31.8.18 run -d -p 8088:8080 cutomimage"      

 
            }
        }
    }
 }
}
