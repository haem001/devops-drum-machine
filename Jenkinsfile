pipeline {
  agent any
  stages {
    stage('Compile') {
      agent any
      steps {
        sh 'sudo npm install'
  
      }
    }
    stage('Build') {
      agent any
      steps {
        sh 'sudo npm run build'
      }
    }
        stage('Archive Artifacts') {
          steps {
            archiveArtifacts '**/public/assets/**'
          }
        }

    stage('Deploy') {
      steps {
        sleep 10
        sh 'sudo curl http://labbnc13vm3.canadacentral.cloudapp.azure.com:8008'
      }
    }
}
  }
