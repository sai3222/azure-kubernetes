pipeline {
  agent any

  stages {
      stage('Build Artifact') {
            steps {
              sh "mvn clean package -DskipTests=true"
              archive 'target/*.jar' //so that they can be downloaded later
            }
        } 
      stage('Unit test -junit test and jacaco') {
            steps {
              sh "mvn test"
            }
           post {
	      always {
		  junit 'target/surefire-reports/*.xml'
		  jacaco execPattern: 'target/jacaco.exec'
	     }
           }	
      }

    }
}
