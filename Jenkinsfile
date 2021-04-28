pipeline{
	agent any
	stages{
		stage("Pull Latest Image"){
			steps{
				sh "docker pull anishst/selenium-docker"
			}
		}
		stage("Start Grid"){
			steps{
				sh "docker-compose up -d hub chrome firefox"
			}
		}
		stage("Run Test"){
			steps{
				// show only logs for the test modules
				sh "docker-compose up saucedemo-module duck-search-module"
			}
		}
	}
	post{
		always{
			// archiveArtifacts artifacts: 'reports/**' # NOT WORKING
			sh "docker-compose down"
			// sh "sudo rm -rf reports/"
		}
	}
}