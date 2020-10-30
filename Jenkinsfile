pipeline {
  agent any
  stages {
    stage('BUILD AND TEST') {
      steps {
        sh '''source /var/lib/jenkins/source_this
        
conda create --yes -n $BUILD_TAG python=3.7

export QUANT_HOME=$(pwd)

conda activate $BUILD_TAG

conda install --force-reinstall -y --file requirements.txt

cd $GUROBI_HOME'''
      }
    }

  }
  environment {
    PATH = '/var/lib/jenkins/miniconda3/bin:$PATH'
  }
}