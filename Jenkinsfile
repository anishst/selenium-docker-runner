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
				// start hub and nodes only; this is prevent jenkins job from hanging
				sh "docker-compose up -d hub chrome firefox"
			}
		}
		stage("Run Test"){
			steps{
				// Grid is already running; now Run tests and show only logs for the test modules
				sh "docker-compose up saucedemo-module duck-search-module"
			}
		}
	}
	post{
		always{
			// sh "ls -R"
			// archiveArtifacts artifacts: 'reports/**' // NOT WORKING
			sh "docker-compose down"
			// sh "sudo rm -rf reports/"
		}
	}
}