node {
   stage('Get Source') {
      // copy source code from local file system and test
      // for a Dockerfile to build the Docker image
      git credentialsId: '66f4235d-971a-410d-997f-139ad7a552ed', url: 'https://github.com/hirudevops/flask-app.git'
      if (!fileExists("Dockerfile")) {
         error('Dockerfile missing.')
      }
   }
   stage('ssh') {
    // some block
    sshPublisher(publishers: [sshPublisherDesc(configName: 'dockerhost', transfers: [sshTransfer(cleanRemote: false, excludes: '', execCommand: '''cd /var/lib/docker/volumes/jenkins_jenkins_data/_data/workspace/flask-app_Docker
    /usr/bin/docker duild -t flask-app .
    /usr/bin/docker run -dit --name flask-app -p 8000:8000 flask-app''', execTimeout: 120000, flatten: false, makeEmptyDirs: false, noDefaultExcludes: false, patternSeparator: '[, ]+', remoteDirectory: '', remoteDirectorySDF: false, removePrefix: '', sourceFiles: '/var/lib/docker/volumes/jenkins_jenkins_data/_data/workspace/flask-app_Docker')], usePromotionTimestamp: false, useWorkspaceInPromotion: false, verbose: false)])
    }
}
