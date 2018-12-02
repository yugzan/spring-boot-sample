pipeline {
  agent any
  stages {
    stage('checkout project') {
      steps {
        checkout scm
      }
    }
  }
  post {
    always {
      echo 'I will always say Hello again!'
      sh "docker-compose run clean"

    }

    success {
      echo 'success!'

    }

    failure {
      echo 'failure!'

    }

  }
}