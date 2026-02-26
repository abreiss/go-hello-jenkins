pipeline {
  agent { label 'nico-jenkins-agent' }

  environment {
    // Make Go builds more reproducible in CI
    CGO_ENABLED = '0'
  }

  stages {
    stage('Checkout') {
      steps {
        checkout scm
      }
    }

    stage('Build') {
      steps {
        sh '''
          set -euo pipefail
          go version
          go env
          go mod tidy
          go build -o hello ./...
        '''
      }
    }

    stage('Run') {
      steps {
        sh '''
          set -euo pipefail
          ./hello
        '''
      }
    }
  }

  post {
    always {
      // optional: keep the built binary as a build artifact
      archiveArtifacts artifacts: 'hello', fingerprint: true
    }
  }
}
