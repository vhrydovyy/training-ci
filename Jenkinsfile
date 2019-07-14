pipeline {
  agent {
    node {
      label 'slave'
    }

  }
  stages {
    stage('Echo Some Text') {
      steps {
        sh 'echo "Some text 123"'
      }
    }
    stage('Git Checkout') {
      steps {
        git(url: 'https://github.com/pavlobornia/training-ci', branch: 'master', credentialsId: 'abf15cef-c50d-426c-bd68-01efff095f62')
      }
    }
    stage('Run app') {
      steps {
        dir(path: 'flask-app') {
          sh 'docker-compose up -d --build'
        }

      }
    }
  }
}