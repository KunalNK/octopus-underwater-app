pipeline {
  agent none

  stages {
    stage('Test') {
        agent {
            ecs {
                // inheritFrom 'label-of-my-preconfigured-template'
                cpu 2048
                memory 4096
                image '502629635618.dkr.ecr.ap-south-1.amazonaws.com/jenkins-cicd:13'
                // logDriver 'fluentd'
                // logDriverOptions([[name: 'foo', value:'bar'], [name: 'bar', value: 'foo']])
                portMappings([[containerPort: 22, hostPort: 22, protocol: 'tcp'], [containerPort: 443, hostPort: 443, protocol: 'tcp']])
            }
        }
        steps {
            sh 'echo hello'
        }
    }
  }
}