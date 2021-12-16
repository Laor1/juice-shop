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
			sh 'gitleaks --access-token=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 --repo-url=https://github.com/Laor1/juice-shop --report=/home/ubuntu/results/testy.json'
			sh 'cat /home/ubuntu/results/testy.json'
      }
	}	
	  stage('OWASP-Dependency-Check') {
		steps {
			dependencyCheck additionalArguments: 'scan="https://github.com/Laor1/juice-shop.git" --format HTML', odcInstallation: '6.5.0'
			sh 'mv /var/lib/jenkins/workspace/Full@2/./dependency-check-report.html /home/ubuntu/results/dependency-check-report.html'
		}
	  }  
}
}	
