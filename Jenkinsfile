pipeline {
  environment {
    registry = '502629635618.dkr.ecr.ap-south-1.amazonaws.com/jenkins-cicd'
    registryCredential = 'aws-credentials'
    dockerImage = ''
  }
  agent any
  stages {
    stage('Building image') {
      steps{
        script {
          dockerImage = docker.build registry + ":$BUILD_NUMBER"
        }
      }
    }
    stage('Deploy image') {
        steps{
            script{
                docker.withRegistry("https://" + registry, "ecr:ap-south-1:" + registryCredential) {
                    dockerImage.push()
                }
            }
        }
    }
  }
}