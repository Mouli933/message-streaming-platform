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
        sh '''
        docker login -u thota372 -p mOULI@6928
        docker push $BACKEND_IMAGE
        docker push $FRONTEND_IMAGE
        '''
      }
    }
  }
}
