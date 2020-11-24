pipeline {
  
  agent any

  environment {
    dockerImage = ''
  }

    stages {
        stage('Checkout Source') {
            steps {
                git branch: 'main', url: 'https://github.com/BBRathnayaka/docker-jenkins-integration-sample.git'
            }
        }
    }
}
