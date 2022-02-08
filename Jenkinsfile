pipeline {
    agent any

    tools {
        maven "maven3.8"
    }

    stages {
        stage ('Build') {
            steps {
                git branch: 'main', url: 'https://github.com/sagar27492/Hospital.git'
		withMaven(maven : 'apache-maven-3.6.1') {
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
                sh "mvn veryfy -DskipUnitTest"
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
