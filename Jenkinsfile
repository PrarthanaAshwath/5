pipeline
{
	agent any
	tools{
		maven 'maven'
	}
	stages{
		stage('Checkout')
		{
			steps{
				git branch:'master',url:'https://github.com/PrarthanaAshwath/5.git'
			}
		}
		stage('Build')
		{
			steps{
				sh 'mvn clean package'
			}
		}
		stage('Archive')
		{
			steps{
				archiveArtifacts artifacts: 'target/*.war' ,fingerprint: true
			}
		}
		stage('Deploy')
		{
			steps{
				sh 'ansible-playbook -i ansible/hosts.ini ansible/deploy.yml'
			}
		}
	}
}

		
