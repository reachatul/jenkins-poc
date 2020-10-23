pipeline {
  agent any
  stages {
    stage('Test Script') {
      steps {
        sh '''python3 --version
python3 -m pip freeze
echo $BUILD_TAG
ls
pwd
cd ..
ls
cd ../..
ls'''
      }
    }

  }
  triggers {
    pollSCM('*/5 * * * 1-7')
  }
}