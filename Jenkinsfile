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
        sh 'npm install'
        sh 'npm run build'
        sh 'docker build -t my-node-app .'
      }
    }
    stage('Deploy') {
      environment {
        DOCKER_HOST = 'tcp://docker:2375'
        IMAGE_NAME = 'my-node-app'
      }
      steps {
        sh 'docker-compose up -d'
      }
    }
  }
}
