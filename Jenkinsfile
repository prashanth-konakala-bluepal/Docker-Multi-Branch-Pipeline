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
								 sh "mv /var/lib/jenkins/workspace/Docker-Multi-Containers_main/webapp/target/*.war /var/lib/jenkins/workspace/Docker-Multi-Containers_main/webapp/target/master.war"
								}
						}
					stage("Deploying to Dev")
						{
						 	steps
								{
								 sshagent(['Docker'])
										{
										 sh """
										 	scp -o StrictHostKeyChecking=no /var/lib/jenkins/workspace/Docker-Multi-Containers_main/webapp/target/master.war ubuntu@3.138.124.225:0648501e6a1a:/opt/tomcat/webapps/
										    """
										}
								}
						}
				}	
		}
