pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh '''
        source /var/lib/jenkins/source_this
        PATH="/var/lib/jenkins/miniconda3/bin:$PATH"
        eval "$(conda shell.bash hook)"
        conda create --yes -n $BUILD_TAG python=3.7
        export QUANT_HOME=$(pwd)
        # eval "$(conda shell.bash hook)"
        bash
        conda activate $BUILD_TAG
        conda install --force-reinstall -y --file requirements.txt
        cd $GUROBI_HOME
        exit
        '''
      }
      }
    }
  post{
      always{
        sh '''
        bash
        conda remove --yes -n $BUILD_TAG --all
        rm -rf /var/lib/jenkins/miniconda3/envs/$BUILD_TAG
        '''
      }
    }
  triggers {
    pollSCM('*/5 * * * 1-7')
  }
}
