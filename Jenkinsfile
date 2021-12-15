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
			sh 'gitleaks --repo=https://github.com/Laor1/juice-shop --access-token=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 --report=/home/testy.json'
			sh 'cat /home/testy.json'
      }
	}	
	  stage('OWASP-Dependency-Check') {
		steps {
			dependencyCheck additionalArguments: 'scan="https://github.com/Laor1/juice-shop.git" --format HTML', odcInstallation: '6.5.0'
		}
	  }  
}
}	
