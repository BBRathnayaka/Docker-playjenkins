pipeline {
  
  agent any

  environment {
    registry = 'localhost:5000/jenkins/docker-playjenkins'
    dockerImage = ''
  }

  stages {
        
    stage('Checkout Source') {
      steps {
                git branch: 'main', url: 'https://github.com/BBRathnayaka/Docker-playjenkins.git'
            }
    }

    stage('Build image') {
      steps {
        script {
          dockerImage = docker.build registry
        }

      }
    }

    stage('Push Image') {
      steps {
        script {
          docker.withRegistry( "" ) {
            dockerImage.push()
          }
        }

      }
    }

    stage('Deploy App') {
      steps {
        sh 'docker rm -f docker-playjenkins'
        sh 'docker run --name docker-playjenkins -d -p 8888:80 localhost:5000/jenkins/docker-playjenkins'
        sh 'echo "Devloped here: http://localhost:8888/ "'
        }
    }
  }
}
