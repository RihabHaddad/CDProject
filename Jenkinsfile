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
	                 stage('docker') {
                                 steps {
                                          script{
                	sh "ansible-playbook ansible/docker.yml -i ansible/inventory/host.yml "
                }
            }

        }
            stage('Grafana') {
                                 steps {
                                          script{
                	sh "ansible-playbook ansible/grafana.yml -i ansible/inventory/host.yml -e ansible_become_password=root  "
                }
            }

        }
                 
    }
}
