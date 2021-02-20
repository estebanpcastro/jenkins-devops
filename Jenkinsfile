//node {
//  stage('Build') {
//    echo "Build"
//  }
//  stage('Test') {
//    echo "Test"
//  }
//  stage('Integration stage') {
//    echo "integretion stage"
//  }
//}

pipeline {
//  agent {docker { image 'node:13.8'} }
  agent any
  environment {
    dockerHome = tool 'myDocker'
    dockerHome = tool 'myMaven'
    PATH = "$dockerHome/bin:$mavenHome/bin:$PATH"
  }
  stages {
    stage('Build') {
      steps {
        sh 'mvn --version'
        sh 'docker version'
        echo 'Build'
        echo "Path - $PATH"
      }
    }
  }

}
