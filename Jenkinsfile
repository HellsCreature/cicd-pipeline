pipeline {
  agent any
  stages {
    stage('build') {
      steps {
        sh 'sh ./scripts/build.sh'
      }
    }

    stage('test') {
      steps {
        sh 'sh ./scripts/test.sh'
      }
    }

    stage('image build') {
      steps {
        sh 'sh docker build -t arsl/cicdimage'
      }
    }

    stage('image push') {
      steps {
        sh '''sh docker.withRegistry(\'https://registry.hub.docker.com\', \'docker_hub_creds_id\')
        { 
          app.push("arsl/cicdimage") 
          app.push("latest") 
        }'''
      }
    }

  }
}
