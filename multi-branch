pipeline{
agent any 
tools {
    maven 'maven'
}
stages{
    
    stage('code checkout'){
        steps{
            git 'https://github.com/mahesh331/maven-web-application.git'
  }
  }
    stage('sonar'){
        steps{
            sh 'mvn sonar:sonar'
  }
  }
    stage('build'){
        steps{
            sh 'mvn clean package'
  }
  }
    stage('publish to nexus'){
        steps{
            sh 'mvn deploy'
  }
  }
  stage('deploy to tomcat'){
        steps{
            sshagent(['vasu']) {
            sh 'scp -o StrictHostKeyChecking=no target/*.war ec2-user@3.84.30.108:/opt/apache-tomcat-9.0.58/webapps/'
    
  }
  }
  }
  
  
}
}
