pipeline {
  agent { label 'nico-jenkins-agent' }

  stages {
    stage('Build') {
      steps {
        sh 'go build -o hello .'
      }
    }

    stage('Run') {
      steps {
        sh './hello'
      }
    }
  }
}
