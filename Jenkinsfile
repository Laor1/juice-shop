pipeline {
  agent any
  stages {
    stage('Initialize') {
      steps {
        sh '''

        echo "PATH = ${PATH}"
        echo "M2_HOME = ${M2_HOME}"

        '''
      }
    }
	stage('Check-Gitleaks') {
		steps {
		    sh 'rm -rf /home/testy.json'
			sh 'gitleaks --repo=https://github.com/Laor1/juice-shop --report=/home/testy.json'
			sh 'cat /home/testy.json'
      }
    }
}
}	
