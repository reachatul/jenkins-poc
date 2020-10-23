pipeline {
  agent any
  stages {
    stage('Test Script') {
      steps {
        sh '''python3 --version
python3 -m pip freeze
echo $BUILD_TAG'''
      }
    }

  }
  triggers {
    pollSCM('*/5 * * * 1-7')
  }
}