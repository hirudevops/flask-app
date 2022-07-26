node {
   stage('Get Source') {
      // copy source code from local file system and test
      // for a Dockerfile to build the Docker image
      git credentialsId: 'github-key', url: 'https://github.com/hirudevops/flask-app.git'
      if (!fileExists("Dockerfile")) {
         error('Dockerfile missing.')
      }
   }
   stage('run docker container') {
    // some block
    sshPublisher(publishers: [sshPublisherDesc(configName: 'docker-host', transfers: [sshTransfer(cleanRemote: false, excludes: '',
    execCommand: '''cd /jenkins/jenkins_home/workspace/flask_app-demo-pipeline
    /usr/bin/docker rm flask-app -f
    /usr/bin/docker build -t flask-app .
    /usr/bin/docker run -dit --name flask-app -p 8000:8000 flask-app''',
    execTimeout: 120000, flatten: false, makeEmptyDirs: false, noDefaultExcludes: false, patternSeparator: '[, ]+', remoteDirectory: '', remoteDirectorySDF: false, removePrefix: '', sourceFiles: '')], usePromotionTimestamp: false, useWorkspaceInPromotion: false, verbose: false)])
    }
}
