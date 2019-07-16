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
    stage('Run Tests') {
      steps {
        dir(path: 'flask-app') {
          sh '''docker-compose down
docker-compose build flask-app
docker-compose run flask-app pytest -v --junit-xml=/var/opt/junit-report/report.xml
docker-compose down'''
          junit 'flask-app/junit-report/report.xml'
          sh '''# Cleanup Step

sudo rm -rf flask-app/junit-report'''
        }

      }
    }
  }
}