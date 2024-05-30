pipeline {
  agent none
  stages {
    stage('Maven Install') {
      agent {
        docker {
          image 'maven:3.5.0'
        }
      }
      steps {
        sh 'mvn clean install'
      }
    }
    stage('Docker Build') {
      agent any
      steps {
        sh 'docker build -t shanem/spring-petclinic:latest .'
      }
    }
    stage('Docker Push') {
      agent any
      steps {
      script{
                   withDockerRegistry(credentialsId: 'docker-cred') {
                    sh "docker tag santa123 sajalsharma125/new-secret:latest"
                    sh "docker push sajalsharma125/new-secret:latest"
      
      }
      }
    }
  }
}
