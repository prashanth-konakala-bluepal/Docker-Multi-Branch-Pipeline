pipeline{	
		 agent
	
		 stages
				{
					stage("Git Checkout")
						{
						 steps
								{
								 git branch: 'main', url: 'https://github.com/prashanth-konakala-bluepal/Multi-Branch-Pipeline.git'
								}
						}
					stage("Maven Build")
						{
						 steps
								{
								 sh "mvn clean package"
								 sh "mv /var/lib/jenkins/workspace/Multi-Branch-Pipeline_main/webapp/target/*.war /var/lib/jenkins/workspace/Multi-Branch-Pipeline_main/webapp/target/main.war"
								}
						}		
					stage("Deploying to Dev")
						{
						 steps
								{
								 sshagent(['Tomcat_server-1'])
										{
										 sh """
										
											scp -o StrictHostKeyChecking=no /var/lib/jenkins/workspace/Multi-Branch-Pipeline_main/webapp/target/main.war ubuntu@3.137.183.211:/opt/tomcat/webapps/
																					
										"""
										}
								}
						}
				}	
		}
