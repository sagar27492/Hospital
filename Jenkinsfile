pipeline {
    agent any

    tools {
        maven "maven3.8"
    }

    stages {
        stage ('Build') {
            steps {
		        withMaven(maven : 'maven3.8') {
			        sh 'mvn install -DskipTests'
		        }
            } 
        }
        stage('unit test') {
            steps {
                sh "mvn test"
            }
        }
        stage('integration test') {
            steps {
                sh "mvn verify -DskipUnitTest"
            }
        }
        stage('static code analysis'){
            steps {
                sh "mvn checkstyle:checkstyle"
            }
        }
    //     stage('CODE ANALYSIS with SONARQUBE') {
	          
	// 		  environment {
	//              scannerHome = tool 'sonarscanner4'
	//           }
	
	//           steps {
	//             withSonarQubeEnv('sonar-pro') {
	//                sh '''${scannerHome}/bin/sonar-scanner -Dsonar.projectKey= \
	//                    -Dsonar.projectName= \
	//                    -Dsonar.projectVersion=1.0 \
	//                    -Dsonar.sources=src/ \
	//                    -Dsonar.java.binaries= \
	//                    -Dsonar.junit.reportsPath= \
	//                    -Dsonar.jacoco.reportsPath= \
	//                    -Dsonar.java.checkstyle.reportPaths='''
	//             }
	
	//             timeout(time: 10, unit: 'MINUTES') {
	//                waitForQualityGate abortPipeline: true
	//             }
	//           }
	//         }

    }
}
