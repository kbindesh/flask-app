pipeline {
  agent any

  stages{
    stage('Building an Image'){
      steps{
        sh "docker image build -t kbindesh/flaskapp:$BUILD_NUMBER ."
        echo "Successfully build an Image"
        sh "docker image ls"
      }
    }
  }
}