pipeline {
  agent any
  stages {
    stage('checkout project') {
      steps {
        checkout scm
      }
    }
    stage('test') {
      steps {
        sh 'docker-compose run test'
      }
    }
    stage('report') {
      steps {
        junit 'target/surefire-reports/*.xml'
      }
    }
    stage('package') {
      steps {
        sh 'docker-compose run package'
      }
    }
    stage('package') {
      steps {
        sh 'docker-compose run clean'
      }
    }    
    stage('archive') {
      steps {
        archiveArtifacts 'target/spring-boot-sample-data-rest-0.1.0.jar'
      }
    }
    stage('deploy') {
      steps {
        sh '''make build-docker-prod-image
docker push localhost:5000/java_sample_prod
make deploy-production-ssh
'''
      }
    }
  }
  post {
    always {
      echo 'I will always say Hello again!'

    }

    success {
      echo 'success!'

    }

    failure {
      echo 'failure!'

    }

  }
}