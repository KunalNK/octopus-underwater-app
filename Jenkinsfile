pipeline {
    agent any
    options {
        skipStagesAfterUnstable()
    }
    stages {
         stage('Clone repository') { 
            steps { 
                script{
                checkout scm
                }
            }
        }

        stage('ECR login') { 
            steps { 
                sh 'aws ecr get-login-password --region ap-south-1 | docker login --username AWS --password-stdin 502629635618.dkr.ecr.ap-south-1.amazonaws.com'
            }
        }

        stage('Build') { 
            steps { 
                sh 'docker build -t jenkins-cicd .'
            }
        }
        stage('Test'){
            steps {
                 echo 'Empty'
            }
        }
        stage('Deploy') {
            steps {
                sh 'docker tag jenkins-cicd:latest 502629635618.dkr.ecr.ap-south-1.amazonaws.com/jenkins-cicd:latest'
                sh 'docker push 502629635618.dkr.ecr.ap-south-1.amazonaws.com/jenkins-cicd:latest'
                }
            }
        }
    }
}