pipeline {
    agent any

    tools {
        maven "maven3.8"
    }

    stages {
        stage('checkout') {
            steps {
                // Get some code from a GitHub repository
                git 'https://github.com/sagar27492/Hospital.git'
            }
        }
        stage('Build') {
            steps {
                sh "mvn clean install -DskipTests"
            }
            post {
                success {
                    echo "Now archiving artifact"
                    archiveArtifacts 'target/*.jar'
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
