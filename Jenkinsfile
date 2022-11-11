pipeline
{
	agent any 
		stages {
			stage('Pull') {
				steps{
					script{
						checkout([$class: 'GitSCM' , branches: [[name: '*/main']],
							userRemoteConfigs: [[ 
								url: 'https://github.com/RihabHaddad/CDProject.git']]])
				}
			}
		}
    }
}
