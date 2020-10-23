pipeline {
  agent any
  triggers {
        pollSCM('*/5 * * * 1-7')
    }
  stages {
    stage('') {
      steps {
        build 'python3 --version'
      }
    }

  }
}
