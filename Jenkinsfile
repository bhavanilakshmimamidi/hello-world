pipeline {
  agent any
  
  tools {
  maven 'maven'
  }
  stages {

  stage ('Checkout') {
          steps {
            checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[credentialsId: '69117607-57a8-4cf4-a433-c93d9e9d27f6', url: 'https://github.com/bhavanilakshmimamidi/hello-world.git']]])	 
		}
	}
    stage ('Build'){
      steps {
      sh 'mvn clean install'
            }
    } 
    stage ('DEV Deploy') {
      steps {
      echo "deploying to tomcat "
      deploy adapters: [tomcat9(credentialsId: 'be75ce54-d908-48fe-8ae8-eebf2dd97fa6', path: '', url: 'http://15.206.166.170:8090/')], contextPath: 'sample', war: '**/*war'
      }
    }
  }
    
}
