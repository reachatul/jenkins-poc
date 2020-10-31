pipeline {
  agent any
  stages {
    stage('Test Script') {
      steps {
        '''
        source /var/lib/jenkins/source_this

	PATH="/var/lib/jenkins/miniconda3/bin:$PATH"
	
	eval "$(conda shell.bash hook)"
        
        conda create --yes -n $BUILD_TAG python=3.7

        export QUANT_HOME=$(pwd)
	
	eval "$(conda shell.bash hook)"

        conda activate $BUILD_TAG

        conda install --force-reinstall -y --file requirements.txt

        cd $GUROBI_HOME


        '''
      }
    }

  }
  triggers {
    pollSCM('*/5 * * * 1-7')
  }
}
