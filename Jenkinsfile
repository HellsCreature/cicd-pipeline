pipeline {
  agent any
  stages {
    stage('build') {
      steps {
        sh '''







sh \'./scripts/build.sh\''''
      }
    }

    stage('test') {
      steps {
        sh 'sh \'./scripts/test.sh\''
      }
    }

    stage('image build') {
      steps {
        sh 'sh \'docker build -t arseniy/cicdimage\''
      }
    }

  }
}