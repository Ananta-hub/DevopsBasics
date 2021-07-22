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
                sshagent(['34.201.11.234']) {
                  sh 'ssh -o StrictHostKeyChecking=no -l ec2-user@34.201.11.234 uname -a'      

 
            }
        }
    }
 }
}
