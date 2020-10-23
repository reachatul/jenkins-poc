pipeline {
  agent any
  stages {
    stage('error') {
      steps {
        sh '''python3 --version
python3 -m pip freeze'''
      }
    }

  }
  triggers {
    pollSCM('*/5 * * * 1-7')
  }
}