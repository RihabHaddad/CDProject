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
		        stage('Build') {
	    	                steps{
	     		                script{
	     	        
	                  sh " ansible-playbook ansible/build.yml  -i /ansible/inventory/host.yml "
	           }
	        }
	    }
	                 stage('Docker') {
                                 steps {
                                          script{
                	sh "ansible-playbook ansible/docker.yml -i ansible/inventory/host.yml "
                }
            }

        }
         stage('Docker-Registry') {
                                 steps {
                                          script{
                	sh "ansible-playbook ansible/docker-registry.yml -i ansible/inventory/host.yml "
                }
            }

        }
        
         stage('Node-exporter') {
                                steps {
                                         script{
                	sh "ansible-playbook ansible/node_exporter.yml -i ansible/inventory/host.yml -e ansible_become_password=root "
                }
            }

        }   
                 
    }
}
