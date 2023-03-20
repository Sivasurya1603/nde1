pipeline {
  agent any
  
  stages {
    stage('Checkout') {
      steps {
        checkout scm
      }
    }
    stage('Build') {
      steps {
        bat 'npm install'
        bat 'npm run build'
        bat 'docker build -t my-node-app .'
      }
    }
    stage('Deploy') {
      environment {
        DOCKER_HOST = 'tcp://docker:2375'
        IMAGE_NAME = 'my-node-app'
      }
      steps {
        bat 'docker-compose up -d'
      }
    }
  }
}
