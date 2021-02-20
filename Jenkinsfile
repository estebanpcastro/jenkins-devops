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
    mavenHome = tool 'myMaven'
    //PATH = "$dockerHome/bin:$mavenHome/bin:$PATH"
  }
  stages {
    stage('Build') {
      steps {
//        sh 'mvn --version'
//        sh 'docker version'
        echo 'Build'
        echo "Path - $PATH"
      }
    }
    stage('Build Docker Image') {
      steps {
//        "docker build -t int28min/currency-exchange-devos:$env.BUIL_TAG"
          script {
            dockerImage = docker.build("int28min/currency-exchange-devos:${env.BUIL_TAG}")
          }
      }
    }
    stage('Push Docker Image') {
      steps {
        script {
            docker.withRegistry('', 'dockerhub') {
              dockerImage.push();
              dockerImage.push('latest');
            }
          }
      }
    }
  }

}
