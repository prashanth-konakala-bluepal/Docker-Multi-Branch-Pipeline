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
		
								}
						}		
					
				}	
		}
