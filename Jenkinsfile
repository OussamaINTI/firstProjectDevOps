pipeline {
agent any

environment {
  /* 
    Windows: set the ip address of docker host. In my case 192.168.1.12
  */
  SONARQUBE_URL = "http://192.168.1.12"
  SONARQUBE_PORT = "9000"
 }
options {
  skipDefaultCheckout()
 }
 
stages {
stage('SCM'){
 git 'https://github.com/OussamaINTI/devOps'
}

stage('Compile'){
def mvnHome = tool name: 'maven-3' , type: 'maven'
sh "${mvnHome}/bin/mvn package"
}

stage('SonarQube') {
  def mvnHome = tool name: 'maven-3' , type: 'maven'
  sh "${mvnHome}/bin/mvn sonar:sonar -Dsonar.host.url=$SONARQUBE_URL:$SONARQUBE_PORT"
    }
 }
}
