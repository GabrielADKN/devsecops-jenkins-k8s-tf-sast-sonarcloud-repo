pipeline {
  agent any
  tools { 
        maven 'Maven_3_2_5'  
    }
   stages{
    stage('CompileandRunSonarAnalysis') {
            steps {	
		sh 'mvn clean verify sonar:sonar -Dsonar.projectKey=rieladkn -Dsonar.organization=rieladkn -Dsonar.host.url=https://sonarcloud.io -Dsonar.token=1de648171eccf1501eb8807f2db9b6f75b13f058'
			}
        } 
  
	stage('RunSCAAnalysisUsingSnyk') {
            steps {		
				withCredentials([string(credentialsId: 'SNYK_TOKEN', variable: 'SNYK_TOKEN')]) {
					sh 'mvn snyk:test -fn'
				}
			}
	}
    }		
}
