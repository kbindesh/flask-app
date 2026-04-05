pipeline {
  agent any

  stages{
    stage('Building an Image'){
      sh "docker image build -t kbindesh/flaskapp:$BUILD_NUMBER"
    }
    stage('Connecting to Registry'){}
    stage('Pushing the Image'){}
  }
}