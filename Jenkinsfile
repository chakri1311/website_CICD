properties([pipelineTriggers([githubPush()])])

pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        echo 'Building..'
        build 'testmvn'
      }
    }
    stage('Test') {
      steps {
        echo 'Testing..'
      }
    }
    stage('Deploy') {
      steps {
        echo 'Deploying....'
      }
    }
  }
}
