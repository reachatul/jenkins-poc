pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh '''
        export GUROBI_HOME="/opt/gurobi903/linux64"
        export PATH="${PATH}:${GUROBI_HOME}/bin"
        export LD_LIBRARY_PATH="${LD_LIBRARY_PATH}:${GUROBI_HOME}/lib"
        PATH="/var/lib/jenkins/miniconda3/bin:$PATH"
        export QUANT_HOME=$(pwd)
        eval "$(conda shell.bash hook)"
        conda create --yes -n $BUILD_TAG python=3.7
        conda activate $BUILD_TAG
        conda install --force-reinstall -y --file requirements.txt
        cd $GUROBI_HOME
        sudo env "PATH=$PATH" /var/lib/jenkins/miniconda3/envs/$BUILD_TAG/bin/python setup.py install
        cd $QUANT_HOME
        ls
        exit
        '''
      }
      }
    }

  post{
      always{
        sh '''
        PATH="/var/lib/jenkins/miniconda3/bin:$PATH"
        bash
        conda remove --yes -n $BUILD_TAG --all
        sudo rm -rf /var/lib/jenkins/miniconda3/envs/$BUILD_TAG
        exit
        '''
      }
    }
  triggers {
    pollSCM('*/5 * * * 1-7')
  }
}
