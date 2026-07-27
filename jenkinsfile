pipeline{
  agent any
  stages {
    stage('clone'){
      steps{
        checkout scm
      }
    }
    stage('Build Docker image'){
      steps{
        sh 'docker build -t demo-image .'
      }
    }
    stage('run container'){
      steps{
        sh '''
        docker rm -f demo-container || true
        docker run -d --name demo-container -p 8080:80 demo-image
        '''
      }
    }
  }
}
