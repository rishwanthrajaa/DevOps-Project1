pipeline {
   agent any

   stages {
      stage('compile') {
         steps {
            git 'https://github.com/rishwanthrajaa/DevOps-Project1.git'
            maven 'mvn compile'
         }
      }
      stage('test') {
         steps {
            maven 'mvn test'
         }
      }
      stage('package') {
         steps {
            maven 'mvn clean'
            maven 'mvn package'
         }
      }
      stage('deploy-docker'){
          steps{
              sh 'cd /var/lib/jenkins/workspace/DevOps-Project1'
              sh 'docker build -t "docker-deploy" .'   
              sh 'docker run -itd --name "docker-deploy-container" -p 3030:8080 docker-deploy'
          }
      }
   }
}
