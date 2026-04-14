pipeline {
  agent any

  environment {
    BACKEND_IMAGE = "thota372/backend:${BUILD_NUMBER}"
    FRONTEND_IMAGE = "thota372/frontend:${BUILD_NUMBER}"
  }

  stages {

    stage('Build Images') {
      steps {
        sh 'docker build -t $BACKEND_IMAGE ./backend'
        sh 'docker build -t $FRONTEND_IMAGE ./frontend'
      }
    }

    stage('Push Images') {
      steps {
        script {
          docker.withRegistry('', 'docker-cred') {
            docker.image("$BACKEND_IMAGE").push()
            docker.image("$FRONTEND_IMAGE").push()
          }
        }
      }
    }
  }
}
