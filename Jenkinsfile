pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh 'g++ main/pes2ug20cs230.cpp -o op'
        build 'PES2UG20CS230-1'
        echo 'Build Successful'
      }
    }
    stage('Test') {
      steps {
        sh './op'
        echo 'Testing Successful'
      }
    }
    stage('Deploy') {
      when {
        expression {
          currentBuild.result == null || currentBuild.result == 'SUCCESS' 
        }
      }
      steps {
        echo 'Deployment Successful'
      }
    }
  }
  post {
    failure {
      echo 'Pipeline failed'
    }
  }
}
