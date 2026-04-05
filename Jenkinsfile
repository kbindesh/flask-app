pipeline {
  agent any

  environment {
    DOCKERHUB_CREDS = 'docker_creds'
    IMAGE_NAME = 'kbindesh/flaskapp'
  }

  stages{
    stage('Building an Image'){
      steps{
        sh "docker image build -t kbindesh/flaskapp:$BUILD_NUMBER ."
        echo "Successfully build an Image"
        sh "docker image ls"
      }
    }
    stage('Connecting to Registry and pushing img'){
      steps{
        script{
          withCredentials([usernamePassword(credentialsId: DOCKERHUB_CREDS, usernameVariable: 'DOCKERHUB_USERNAME', passwordVariable: 'DOCKERHUB_PASSWORD')]){
            sh "docker login -u ${DOCKERHUB_USERNAME} -p ${DOCKERHUB_PASSWORD}"
            sh "docker image push kbindesh/flaskapp:$BUILD_NUMBER"
          }
        }
      }
    }
  }
}