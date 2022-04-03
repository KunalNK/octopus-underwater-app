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
        
        stage('Build') { 
            steps { 
                script{
                 app = docker.build("underwater")
                }
            }
        }
        stage('Test'){
            steps {
                 echo 'Empty'
            }
        }
        stage('Deploy') {
            steps {
                script{
                        docker.withRegistry('https://502629635618.dkr.ecr.ap-south-1.amazonaws.com/jenkins-cicd', 'ecr:ap-south-1:aws-credentials') {
                    app.push("latest")
                    }
                }
            }
        }
    }
}
