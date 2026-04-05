pipeline {
  agent any

  environment {
    DOCKERHUB_CREDS = 'docker_creds'
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
        script{
          withCredentials([usernamePassword(credentialsId: DOCKERHUB_CREDS, usernameVariable: 'DOCKERHUB_USERNAME', passwordVariable: 'DOCKERHUB_PASSWORD')]){
            sh "docker login -u ${DOCKERHUB_USERNAME} -p ${DOCKERHUB_PASSWORD}"
          }
        }
      }
    }
  }
}