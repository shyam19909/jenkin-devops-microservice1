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
		dockerHome = tool 'mydocker'
		mavenHome = tool 'myMaven'
		PATH = "$dockerHome/bin:$mavenHome/bin:$PATH"

	}
	stages	{
		stage('Build'){
			steps{
				// sh 'mvn --version'
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
		stage('Test'){
			steps{
				echo "Test"
			}

		}
		stage('Integration Test'){
			steps{
				echo "Integration Test"
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
