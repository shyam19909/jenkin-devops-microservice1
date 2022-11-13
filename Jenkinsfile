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
	agent any
	stages	{
		stage('Build'){
			steps{
				echo "Build"
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
