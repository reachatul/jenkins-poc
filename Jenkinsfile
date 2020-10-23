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
cd /var/lib/jenkins/quanthub/
source source_this
python3 -m pytest --log-cli-level=INFO lib/quantalgos/tests/test_poc.py
'''
      }
    }

  }
  triggers {
    pollSCM('*/5 * * * 1-7')
  }
}