
pipeline {
	agent{
	label{
			label "QA"
			customWorkspace "/mnt/container-1-90"
	     }
	     }
	

	stages {
	

			stage ("slave-ssh"){
				steps { 
				    sh "sudo rm -rf *"
					sh "sudo yum install git -y"
					sh "sudo git init"
					sh "sudo git clone https://github.com/prem0609/gitrepo-container.git"
				}
			}
		       stage ("docker-install") {
					steps{	
						sh "sudo yum install docker -y"
					      sh "sudo systemctl start docker" 
				}
	               }
		       stage ("cont.90-80") {
			steps { 
			    sh "sudo docker rm -f prem"
			    sh "sudo docker system prune -a -f"
	                   sh "sudo docker run -itdp 90:80 --name prem httpd"
	                   sh "sudo chmod -R 777 /mnt/container-1-90/gitrepo-container/index.html"
		           sh "sudo docker cp /mnt/container-1-90/gitrepo-container/index.html prem:/usr/local/apache2/htdocs" 
			}
		}
	    }
	}
