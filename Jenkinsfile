#!groovy
@Library('first-shared-lib@release') _

pipeline {
  agent any
  options {
    // Only keep the 10 most recent builds
    buildDiscarder(logRotator(numToKeepStr:'10'))
  }
  stages {
    stage ('Start') {
      steps {
        // send build started notifications
        sendNotifications 'STARTED'
      }
    }
    stage ('Install') {
      steps {
        // install required bundles
        sh 'echo "Inside Install stage of testingFirstSharedLib git repo"'
      }
    }
    stage ('Build') {
      steps {
        // build
        sh 'echo "Inside Build stage of testingFirstSharedLib git repo"'
      }

      post {
        success {
          // Archive the built artifacts
          sh 'echo "Inside post success block of Build stage of testingFirstSharedLib git repo"'
        }
      }
    }
    stage ('Test') {
      steps {
        // run tests with coverage
        sh 'echo "Inside Test stage of testingFirstSharedLib git repo"'
      }

      post {
        success {
          // publish html
          sh 'echo "Inside post success block of Test stage of testingFirstSharedLib git repo"'
        }
      }
    }
  }
  post {
    always {
      sh 'echo "Inside always post for all stages of testingFirstSharedLib git repo"'
      sendNotifications currentBuild.result
    }
  }
}
