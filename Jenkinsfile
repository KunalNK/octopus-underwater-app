// pipeline {
//   environment {
//     registry = '502629635618.dkr.ecr.ap-south-1.amazonaws.com/jenkins-cicd'
//     registryCredential = 'aws-credentials'
//     dockerImage = ''
//   }
//   agent any
//   stages {
//     stage('Build docker image') {
//       steps{
//         script {
//           dockerImage = docker.build registry + ":$BUILD_NUMBER"
//         }
//       }
//     }
//     stage('Push image to ECR') {
//         steps{
//             script{
//                 docker.withRegistry("https://" + registry, "ecr:ap-south-1:" + registryCredential) {
//                     dockerImage.push()
//                 }
//             }
//         }
//     }
//   }
// }

pipeline {
  agent none

  stages {
    stage('Test') {
        agent {
            ecs {
                inheritFrom 'label-of-my-preconfigured-template'
                cpu 2048
                memory 4096
                image '502629635618.dkr.ecr.ap-south-1.amazonaws.com/jenkins-cicd'
                logDriver 'fluentd'
                logDriverOptions([[name: 'foo', value:'bar'], [name: 'bar', value: 'foo']])
                portMappings([[containerPort: 22, hostPort: 22, protocol: 'tcp'], [containerPort: 443, hostPort: 443, protocol: 'tcp']])
            }
        }
        steps {
            sh 'echo hello'
        }
    }
  }
}