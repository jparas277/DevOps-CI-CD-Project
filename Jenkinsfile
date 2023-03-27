pipeline {
  agent any

  environment {
    DOCKERHUB_CREDENTIALS = credentials('docker-hub-creds')
    REMOTE_SERVER = '3.88.141.67'
    REMOTE_USER = 'ubuntu'            
  }

  // Fetch code from GitHub

  stages {
    stage('checkout') {
      steps {
        git branch: 'main', url: 'https://github.com/palakbhawsar98/JavaWebApp'

      }
    }

   // Build Java application

   // Build docker image in Jenkins


   // Push image to DockerHub registry



   // Pull docker image from DockerHub and run in EC2 instance 

    stage('Deploy Docker image to AWS instance') {
      steps {
        script {
          sshagent(credentials: ['aws-cred']) {
          sh "ssh -o StrictHostKeyChecking=no ${REMOTE_USER}@${REMOTE_SERVER} 'docker stop javaApp || true && docker rm javaApp || true'"
          sh "ssh -o StrictHostKeyChecking=no ${REMOTE_USER}@${REMOTE_SERVER} 'docker pull jparas/javawebapp'"
          sh "ssh -o StrictHostKeyChecking=no ${REMOTE_USER}@${REMOTE_SERVER} 'docker run --name javaApp -d -p 8081:8081 jparas/javawebapp'"
          }
        }
      }
    }
  }
