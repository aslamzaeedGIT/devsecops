pipeline {
  agent any
  tools { 
        maven 'Maven_3.8.4'  
    }
   stages{
    stage('CompileandRunSonarAnalysis') {
            steps {	
		sh 'mvn clean verify sonar:sonar -Dsonar.projectKey=asgbuggywebapp007_asgbuggywebapp -Dsonar.organization=asgbuggywebapp007 -Dsonar.host.url=https://sonarcloud.io -Dsonar.token=353fa8741d01f53d27115715d988f1b6b74e3c1d'
			}
    }
    stage('RunSCAAnalysisUsingSnyk') {
            steps {		
				withCredentials([string(credentialsId: 'snyk-token', variable: 'SNYK_TOKEN')]) {
					sh 'mvn snyk:test -fn'
				}
			}
    }
	


   }
}