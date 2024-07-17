pipeline {
	agent any
	stages {
		stage('Checkout SCM') {
			steps {
				git 'https://github.com/SikesJohn/JenkinsDependencyCheckTest'
			}
		}

		stage('OWASP_Dependency-Check_Vulnerabilities') {
			steps {
				dependencyCheck additionalArguments: '--format HTML --format XML', odcInstallation: 'Default'
				// MUST MATCH THE FILE NAME
				odcInstallation: 'OWASP_Dependency-Check_Vulnerabilities'
			}
		}
	}	
	post {
		success {
			dependencyCheckPublisher pattern: 'dependency-check-report.xml'
		}
	}
}