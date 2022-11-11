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
		       stage('build') {
	    	                steps{
	     		                script{
	     	        
	                  sh " ansible-playbook ansible/build.yml  -i /ansible/inventory/host.yml "
	           }
	        }
	    }
    }
}
