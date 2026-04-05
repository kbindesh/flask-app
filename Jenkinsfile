pipeline {
  agent any

  environment {
    DOCKERHUB_CREDS = credentials('docker_creds')
  }

  stages{
    stage('Building an Image'){
      steps{
        sh "docker image build -t kbindesh/flaskapp:$BUILD_NUMBER ."
        echo "Successfully build an Image"
        sh "docker image ls"
      }
    }
    stage('Connecting to Registry'){
      steps{
        sh "echo $DOCKERHUB_CREDS_PSW | docker login -u DOCKERHUB_CREDS_USR --password-stdin"
        echo "Successfully connected to DockerHub"
      }
    }
  }
}