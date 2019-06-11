pipeline {
  agent any
  stages {
    stage('Compile') {
      agent any
      steps {
        sh 'sudo npm install'
        sh 'sudo npm run build'
      }
    }
    stage('Unit Testing') {
      agent any
      steps {
        sh 'sudo npm test'
      }
    }
    stage('Deploy') {
      
        stage('Archive Artifacts') {
          steps {
            archiveArtifacts '**/public/assets/**'
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
