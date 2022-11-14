// node {
// 	stage('Build') {
// 		echo "Build"
// 	}
// 	stage('Test') {
// 		echo "Test"
// 	}
// 	stage('Integration Test') {
// 		echo "Test"
// 	}
// }

//SCRIPTED
// node{
// 	echo "Build"
// 	echo "Test"
// 	echo "Integration Test"

// }

//Declarative
pipeline {
	// agent any
	agent any
	environment {
		dockerHome = tool 'myDocker'
		mavenHome = tool 'myMaven'
		PATH = "$dockerHome/bin:$mavenHome/bin:$PATH"

	}
	stages	{
		// stage('Build'){
		stage('Checkout'){
			steps{
				sh 'mvn --version'
				sh 'docker version'
				echo "Build"
				echo "PATH -$PATH"
				echo "BUILD_NUMBER - $env.BUILD_NUMBER"
				echo "BUILD_ID - $env.BUILD_ID"
				echo "JOB_NAME - $env.JOB_NAME"
				echo "JOB_TAG  - $env.BUILD_TAG"
				echo "BUILD_URL - $env.BUILD_URL"
			}

		}
		stage('compile'){
			steps {
				sh "mvn clean compile"
			}
		}
		stage('Test'){
			steps{
				sh "mvn test"
			}

		}
		stage('Integration Test'){
			steps{
				sh " mvn failsafe:integration-test failsafe:verify"
			}

		}
		stage('Pacakage'){
			steps{
				sh "mvn pacakge -DskipTests"
			}

		}		
		stage('Build Docker Image'){
			steps {
				// docker build -t shyam19909/currency-exchange-devops:$env.BUILD_TAG
				script{
					dockerImage = docker.build("shyam19909/currency-exchange-devops:$env.BUILD_TAG")
				}
			}
		}
		stage{
			steps{
				script{
					docker.withRegistry('','doeckerhub'){
						dockerImage.push();
						dockerImage.push('latest');
					}
				}
			}
		}


	} 
	post{
		always {
			echo ' I run always'	
		}
		success {
			echo 'when you success'
		}
		failure {
			echo 'when you fail'
		}
	}

}
