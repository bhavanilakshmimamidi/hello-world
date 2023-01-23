
pipeline {
  agent any
  
 /* tools {
  maven 'M2_HOME'
  }*/
  stages {

  stage ('Checkout') {
          steps {
            checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[credentialsId: '69117607-57a8-4cf4-a433-c93d9e9d27f6', url: 'https://github.com/bhavanilakshmimamidi/hello-world.git']]])	 
		}
	}
    stage ('Build'){
      steps {
      sh 'mvn clean package'
            }
    } 
    stage ('DEV Deploy') {
      steps {
      echo "deploying to tomcat "
     deploy adapters: [tomcat9(credentialsId: '431afeec-05a8-4be8-95d1-2fd81191d248', path: '', url: 'http://3.112.198.239:8081/')], contextPath: 'PipelineSample', onFailure: false, war: '**/*.war'
      }
    }
  }
    
}
