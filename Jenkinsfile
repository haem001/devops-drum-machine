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
        stash includes: 'public/', name: 'BuildArtifact'
      }
    }
        stage('Archive Artifacts') {
          steps {
            unstash 'BuildArtifact'
            archiveArtifacts '**/public/assets/**'
            
            sshPublisher(publishers: [sshPublisherDesc(configName: 'docker', transfers: [sshTransfer(cleanRemote: false, excludes: '', execCommand: '', execTimeout: 120000, flatten: false, makeEmptyDirs: false, noDefaultExcludes: false, patternSeparator: '[, ]+', remoteDirectory: '', remoteDirectorySDF: false, removePrefix: 'public', sourceFiles: 'public/')], usePromotionTimestamp: false, useWorkspaceInPromotion: false, verbose: false)])
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
