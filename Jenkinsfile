pipeline {
  agent any
  stages {
    stage('build') {
      steps {
        sh './scripts/build.sh'
      }
    }

    stage('test') {
      steps {
        sh './scripts/test.sh'
      }
    }

    stage('image build') {
      steps {
        sh 'docker build -t arsl/cicdimage'
      }
    }

    stage('image push') {
      steps {
        script {
          docker.withRegistry('https://registry.hub.docker.com', 'docker_hub_creds_id')
          { 
            app.push("arsl/cicdimage") 
            app.push("latest") 
          }
        }
      }
    }

  }
}
