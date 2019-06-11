pipeline {
  agent any
  stages {
    stage('Build') {
      agent any
      steps {
        sh 'npm install'
        sh 'npm run build'
      }
    }
    stage('Unit Testing') {
      agent any
      steps {
        sh 'npm test'
      }
    }
    stage('Deploy') {
      //parallel {
        stage('Deploy') {
          steps {
            sh 'sudo docker run -d --name student1 -p 8008:80 -p 2222:22 iliyan/docker-nginx-sshd'
          }
        }
        stage('Archive Artifacts') {
          steps {
            archiveArtifacts '**/public/'
          }
        }
      }
    }
    stage('Integration testing') {
      steps {
        sleep 10
        sh 'sudo curl localhost'
      }
    }
  }
}