pipeline{	
		 agent { label 'master' }
	
		 stages
				{
					stage("Git Checkout")
						{
						 steps
								{
								 git branch: 'main', url: 'https://github.com/prashanth-konakala-bluepal/Docker-Multi-Branch-Pipeline.git'
								}
						}
					stage("Maven Build")
						{
						 steps
								{
								 sh "mvn clean package"
								 sh "mv /var/lib/jenkins/workspace/Docker-Multi-Branch-Pipeline_main/webapp/target/*.war /var/lib/jenkins/workspace/Docker-Multi-Branch-Pipeline_main/webapp/target/main.war"
								}
						}		
					
				}	
		}
