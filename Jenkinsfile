pipeline {
 agent any

 stages {

  stage('Checkout') {
   steps {
    git 'https://github.com/venkatpokala594/jenkins-java-project.git'
   }
  }

  stage('Build') {
   steps {
    sh '''
    mvn compile
    mvn test
    mvn clean package
    '''
   }
  }

  stage('SonarQube Analysis') {
   steps {
    withSonarQubeEnv('SonarQube') {
     sh '''
     mvn sonar:sonar \
     -Dsonar.projectKey=myapp \
     -Dsonar.host.url=http://44.221.90.69:9000 \
     -Dsonar.login=$sonar-token
     '''
    }
   }
  }

 }
}
