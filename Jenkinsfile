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
										
											scp -o StrictHostKeyChecking=no /var/lib/jenkins/workspace/Docker-Multi-Containers_main/webapp/target/master.war ubuntu@3.142.196.56:/opt/warfiles/master/
											ssh ubuntu@3.142.196.56 docker exec -it 0648501e6a1a /bin/bash
											// ssh ubuntu@3.142.196.56 mv /opt/warfiles/master/master.war 0648501e6a1a:/opt/tomcat/webapps/										
											
											"""
										}
								}
						}
				}	
		}
