pipeline {
    agent any

    tools {
        maven "maven3.8"
    }

    stages {
        stage ('Build') {
            steps {
                git url: 'https://github.com/sagar27492/Hospital.git'
                withMaven {
                    sh "mvn clean install -DskipTests"
                } // withMaven will discover the generated Maven artifacts, JUnit Surefire & FailSafe reports and FindBugs reports
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
            sh "mvn checkstyle:checkstyle"
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

    // }
}
