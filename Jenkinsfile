pipeline {
  agent {
    node {
      label 'master'
    }

  }
  stages {
    stage('Echo Some Text') {
      steps {
        sh 'echo "Some text 123"'
      }
    }
  }
}